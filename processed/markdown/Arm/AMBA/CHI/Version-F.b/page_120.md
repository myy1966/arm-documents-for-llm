#### B2.5.3.3 WriteUnique transaction

This section describes the use of the identifier fields for a WriteUnique transaction.

Figure B2.30 does not show the Memory Tagging supported TagGroupID flow. For TagGroupID transfer details, see B12.5 Write transactions.

Under certain circumstances, the WriteUnique transaction can also include a CompAck response from the Requester to the Completer. In this case, the additional rules for the use of the identifier fields are:

- The TgtID, SrcID, and TxnID identifier fields of the CompAck response from the Requester to the Completer must be the same as the fields used for the write data, that is:

    - The TgtID is set to the same value as the SrcID of the CompDBIDResp response. If separate Comp and DBIDResp responses are given, the TgtID is set to the same value as the SrcID of either the Comp or DBIDResp response because the SrcID value in both must be identical. However, this can be different from the original TgtID of the request if the value has been remapped by the interconnect.
    - The SrcID is a fixed value for the Requester.
    - The TxnID is set to the same value as the DBID value provided in the CompDBIDResp response. If separate Comp and DBIDResp responses are given, the TxnID is set to the same value as the DBID of either the Comp or DBIDResp response because the DBID value in both must be identical.
    - The DBID field in the WriteData and in the CompAck is not used.
    - If a combined WriteData and CompAck response is sent, the TgtID is set to the same value as the SrcID in the Comp, DBIDResp, or CompDBIDResp, and the TxnID in the combined response is set to the same value as the DBID in Comp, DBIDResp, or CompDBIDResp.

- The Completer must receive all items of write data and the CompAck response before reusing the same DBID value for another transaction.

Figure B2.30 shows the identifier value transfer with a combined CompDBIDResp response.