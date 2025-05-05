    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Completer. This also matches the TgtID received.
    - The TxnID is set to the same value as the TxnID of the request.
    - The Completer generates a unique DBID value.

3. The Requester receives the CompDBIDResp response and sends the write data.

    The identifier fields of the write data are generated as follows:

    - The TgtID is set to the same value as the SrcID of the CompDBIDResp response. This can be different from the original TgtID of the request if the value was remapped by the interconnect.
    - The SrcID is a fixed value for the Requester.
    - The TxnID is set to the same value as the DBID value provided in the CompDBIDResp response.
    - The DBID field in the write data is not used.
    - The TgtID, SrcID, and TxnID fields must be the same for all write data packets.

    After receiving the CompDBIDResp response, the Requester can reuse the same TxnID value used in the request packet for another transaction.

4. The Completer receives the write data and uses the TxnID field, which now contains the DBID value that the Completer generated. This helps to determine which transaction to associate the write data.

    After receiving all write data packets, the Completer can reuse the same DBID value for another transaction.

#### B2.5.3.2 WriteNoSnp transaction

This section describes the use of the identifier fields for a WriteNoSnp transaction.

Figure B2.29 does not show the Memory Tagging supported TagGroupID flow. For TagGroupID transfer details, see B12.5 Write transactions.

Figure B2.29 shows the identifier value transfer for separate Comp and DBIDResp. The Completer can opportunistically combine the Comp and DBIDResp into a single CompDBIDResp response. The Requester can opportunistically combine NonCopyBackWriteData with CompAck.