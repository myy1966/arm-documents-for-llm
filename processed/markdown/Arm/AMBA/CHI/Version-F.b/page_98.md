- All responses associated with a previous transaction that have used the same value.
- A RetryAck response for a previous transaction that used the same value.

B2.5 Transaction identifier field flows gives more detailed rules for the different transaction types. The TxnID field is not applicable in a PrefetchTgt request and can take any value.

A value used in the TxnID field of a Request from Home to Subordinate can be reused by Home once all responses that are required to deallocate the request are received or a RetryAck response is received.

A transaction that is retried is not required to use the same TxnID. See B2.9 Request Retry.

### B2.4.3 Data Buffer Identifier, DBID

The DBID field permits the Completer of a transaction to provide its own identifier for a transaction. The Completer sends a response that includes a DBID. The DBID value is used as the TxnID field value in the:

- WriteData response of Immediate Write, CopyBack Write, Combined Write, Atomic, and DVMOp transactions.
- CompData response of Stash transactions for Data Pull purposes.
- CompAck response of Read, Dataless, WriteNoSnp, WriteUnique and Immediate Combined Write transactions that include a CompAck response.

The DBID value used by a Completer in responses of a given transaction must be unique for a given Requester in the following cases:

- DBIDResp or DBIDRespOrd or CompDBIDResp for all Write transactions, except in WriteNoSnpZero and WriteUniqueZero.
- DBIDResp or DBIDRespOrd or CompDBIDResp for all Combined Write transactions.
- DBIDResp or DBIDRespOrd or CompDBIDResp for Atomic transactions.
- DBIDResp or DBIDRespOrd or CompDBIDResp for DVMOp transactions.
- CompData or RespSepData for Read transactions that include CompAck, except in the case when ReadOnce\* and ReadNoSnp do not use the resultant CompAck for deallocation of the request at Home.
- Comp for Dataless transactions that include CompAck.

The DBID value is applicable in the DataSepResp response to Read requests that include CompAck, and it must be the same as the DBID value in the associated RespSepData response.

A Comp response message sent separate from a DBIDResp or DBIDRespOrd message for a Write or Combined Write transaction must include the same DBID field value in the Comp and DBIDResp or DBIDRespOrd message when the two messages originate from the same source.

A Comp response message sent separate from a DBIDResp or DBIDRespOrd message for a Atomic transaction is permitted, but is not required, to include the same DBID field value in the Comp and DBIDResp or DBIDRespOrd message.

A Completer is permitted, but not required, to use the same DBID value for two transactions with different Requesters. A Completer is permitted to reuse a DBID value after it has received all packets required to deallocate a previous transaction that has used the same value. B2.5 Transaction identifier field flows gives more detailed rules for the different transaction types.

The DBID value used by a Snoop Completer in response to a Stash snoop that includes a Data Pull must be unique with respect to:

- The DBID values in other Snoop responses to Stash snoops that use Data Pull.
- The TxnID of any outstanding request from that Snoop Completer.