    - The DBID is set to the same value as the TxnID of the snoop.

4. The RN-F also provides a response to Home, either with or without read data.

    The identifier fields of the response are generated as follows:

    - The TgtID is set to the same value as the SrcID of the snoop.
    - The SrcID is a fixed value for the RN-F.
    - The TxnID is set to the same value as the TxnID of the snoop.
    - The DBID field is not valid.

5. The Requester receives the read data and sends a completion acknowledge, CompAck, response.

    The identifier fields of the CompAck are generated as follows:

    - The TgtID is set to the same value as the HomeNID of the read data.
    - The SrcID is a fixed value for the Requester. This also matches the TgtID that was received.
    - The TxnID is set to the same value as the DBID of the read data.
    - The DBID field is not valid.

> **_NOTE:_** An optional ReadReceipt from the interconnect to Requester can also be included.

#### B2.5.1.4 ID value transfer without Direct Data Transfer

This section gives an example of a Read identifier field flow without DMT or DCT and describes the use of the TxnID and DBID fields for Read transactions.

The Requester and Completer in this example are a Request Node and an HN-F respectively.

The identifier field flow includes an optional ReadReceipt response from the Completer, and an optional CompAck response from the Requester.

For Read transactions that include a CompAck response, the DBID is used by the Completer to associate the CompAck with the original transaction.

A Read transaction that does not include a CompAck response does not require a valid DBID field in the data response.

Figure B2.26 shows the ID value transfer.