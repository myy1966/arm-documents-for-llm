        > **_NOTE:_** The TgtID field can be remapped to a different value by the interconnect.

    - The SrcID is a fixed value for the Requester.
    - The Requester generates a unique TxnID field.

2. The Completer receives the Request packet and determines that a RetryAck response will be sent.

    The identifier fields of the RetryAck response are generated as follows:

    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Completer. This also matches the TgtID received.
    - The TxnID is set to the same value as the TxnID of the request.
    - The DBID field is not valid.
    - The Completer uses a PCrdType value that indicates the type of credit required to retry the transaction.

3. When the Completer is able to accept the retried transaction of a given PCrdType, a credit to the Requester is sent using the PCrdGrant response.

    The identifier fields of the PCrdGrant response are generated as follows:

    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Completer. This also matches the TgtID of the request.
    - The TxnID field is not used and must be set to 0.
    - The DBID field is not used and must be set to 0.
    - The PCrdType value is set to the type required to issue the original transaction again.

4. The Requester receives the credit grant and reissues the original transaction by sending a Request packet.

    The identifier fields of the request are generated as follows:

    - The TgtID is set to either the same value as the SrcID of the RetryAck response, which is also the same as the SrcID of the PCrdGrant response, or the value used in the original request.
    - The SrcID is a fixed value for the Requester.
    - The Requester generates a unique TxnID field. This is permitted, but not required, to be different from the original request that received a RetryAck response.
    - The PCrdType value is set to the PCrdType value in the RetryAck response to the original request, which is also the same as the PCrdType of the PCrdGrant response.

### B2.5.6 Protocol Credit Return transaction

A P-Credit Return transaction uses the PCrdReturn Request to return a granted, but no longer required, credit. The TgtID, SrcID, and TxnID requirements are:

- The Requester sends the Protocol Credit Return transaction by sending a PCrdReturn Request packet. The identifier fields of the request are generated as follows:

    - The TgtID must match the SrcID of the credit that was obtained.
    - The SrcID is a fixed value for the Requester.
    - The TxnID field is not used and must be set to 0.

The PCrdType must match the value of the PCrdType in the original PCrdGrant that was required to issue the original transaction again.

There is no response or use made of the DBID field associated with Protocol Credit Return transactions.