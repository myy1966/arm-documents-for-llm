    - The SrcID is a fixed value for the Completer. This also matches the TgtID received.
    - The TxnID is set to the same value as the TxnID of the request.
    - The HomeNID is a fixed value for the Completer. This also matches the TgtID received.
    - The Completer generates a unique DBID value if ExpCompAck in the request is asserted.

4. The Requester receives the read data and sends a completion acknowledge, CompAck, response.

    The identifier fields of the CompAck are generated as follows:

    - The TgtID is set to the same value as the HomeNID of the read data.
    - The SrcID is a fixed value for the Requester. This also matches the TgtID that was received.
    - The TxnID is set to the same value as the DBID of the read data.
    - The DBID field is not valid.

### B2.5.2 Dataless transactions

For Dataless transactions, except for CleanSharedPersistSep and StashOnceSep, the use of identifier fields is similar to B2.5.1.4 ID value transfer without Direct Data Transfer. The only difference is that the response from the Completer to the Requester is sent as a single packet on the CRSP channel instead of multiple packets on the RDAT channel.

For StashOnceSep transactions, the StashGroupID value is sent in the request from the Request Node to the interconnect and the value is returned in the StashDone and CompStashDone responses. The TxnID value in the StashDone response is inapplicable and must be set to 0.

The description of ID value transfer in a CleanSharedPersistSep transaction follows.

#### B2.5.2.1 ID value transfer in a CleanSharedPersistSep transaction

Figure B2.27 shows how the identifier field values are derived in CleanSharedPersistSep transaction messages that use separate Comp and Persist responses. In Figure B2.27, PCMOSep represents CleanSharedPersistSep.