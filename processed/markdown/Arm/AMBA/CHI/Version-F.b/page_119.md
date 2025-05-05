    - The Requester generates a unique TxnID field.

2. The Completer receives the Request packet and generates a DBIDResp response.

    The identifier fields of the response are generated as follows:

    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Completer. This also matches the TgtID received.
    - The TxnID is set to the same value as the TxnID of the request.
    - The Completer generates a unique DBID value.

3. The Requester receives the DBIDResp response and sends the write data.

    The identifier fields of the write data are generated as follows:

    - The TgtID is set to the same value as the SrcID of the DBIDResp response. This can be different from the original TgtID of the request if the value was remapped by the interconnect.
    - The SrcID is a fixed value for the Requester.
    - The TxnID is set to the same value as the DBID value provided in the DBIDResp response.
    - The DBID field in the write data is not used.
    - The TgtID, SrcID, and TxnID fields must be the same for all write data packets.

4. The Completer receives the write data and uses the TxnID field, which now contains the DBID value that the Completer generated, to determine which transaction the write data is associated with.

5. The Completer generates a Comp response when the transaction is complete.

    The identifier fields of the Comp response must be the same as the DBIDResp response and are generated as follows:

    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Completer. This also matches the TgtID received.
    - The TxnID is set to the same value as the TxnID of the request.
    - The Completer uses the same DBID value as is used in the DBIDResp response.

6. The Requester sends a CompAck message, if required by the transaction, after receiving DBIDResp or Comp.

    The identifier fields of the CompAck are generated as follows:

    - The TgtID is set to the same value as the SrcID of the DBIDResp or Comp response.
    - The SrcID is a fixed value for the Requester. This also matches the TgtID that was received.
    - The TxnID is set to the same value as the DBID of the DBIDResp or Comp response.
    - The DBID field is not valid.

After receiving both the Comp and DBIDResp response, the Requester can reuse the same TxnID value for another transaction.

After receiving all the write data packets, the Completer can reuse the same DBID value for another transaction.

> **_NOTE:_** There is no ordering requirement between the separate DBIDResp and Comp responses. It is required that the values used are identical when the two messages originate from the same source.