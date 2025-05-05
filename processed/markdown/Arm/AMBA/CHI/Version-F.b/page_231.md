**Persist**

- See B2.6.5.1 Ordering requirements for how ReadReceipt is used in an ordered request.
- Applies to ReadNoSnp, ReadNoSnpSep, and ReadOnce* request transactions.
- The RespErr field is applicable and must be set to 0.
- The Resp field is inapplicable and must be set to 0.

See B2.3.1 Read transactions.

**DBIDResp**

- Response sent to signal to the Requester that resources are available to accept the WriteData response.
- DBIDResp response also indicates that the Completer provides certain transaction ordering guarantees. See B2.6.5 Transaction ordering.
- Applies to Write, Combined Write, DVMOp, and Atomic request transactions.
- The response is permitted from Home Node to Request Node and Subordinate Node to both a Home Node and Request Node.
- The RespErr field is applicable and must be set to 0.
- The Resp field is inapplicable and must be set to 0.

See B2.3 Transaction structure.

**DBIDRespOrd**

- Response sent to signal to the Requester that resources are available to accept the WriteData response.
- DBIDRespOrd response also indicates that the Completer provides certain transaction ordering guarantees. See B2.6.5 Transaction ordering.
- Applies to Write, Combined Write, and Atomic request transactions.
- DBIDRespOrd is not permitted in DVM transactions.
- The response is permitted from Home Node to Request Node only.
- The RespErr field is applicable and must be set to 0.
- The Resp field is inapplicable and must be set to 0.

See B2.6.5 Transaction ordering.

- Sent by a Completer for CleanSharedPersistSep transaction to indicate that any data written earlier to the same memory location is made persistent.
- The RespErr field is applicable. See Table B9.5.
- The Resp field is inapplicable and must be set to 0.

See B2.3.2.5 Combined Immediate Write and Persist CMO and B2.3.2.6 Combined CopyBack Write and CMO.

**StashDone**

- Sent by a Completer for StashOnceSep to signal the ordering of the request at the Completer.
- The RespErr field is applicable. See Table B9.6.
- The Resp field is inapplicable and must be set to 0.