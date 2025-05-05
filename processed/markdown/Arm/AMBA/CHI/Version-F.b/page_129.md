> **_NOTE:_** The size of an endpoint address range is IMPLEMENTATION DEFINED. Typically, this is:
>
> - The size of a peripheral device, for a region used for peripherals.
> - The size of a cache line, for a region used for memory.
>
> A Cacheable location can be determined by the assertion of the MemAttr[2] Cacheable bit in the request. A Non-cacheable or Device location can be determined by the deassertion of the MemAttr[2] Cacheable bit in the request.

A component must only give a Comp or CompDBIDResp response when all observers are guaranteed see the result of the atomic operation.

A Comp response in a canceled write only implies that the transaction loop is completed and makes no statement regarding the completion of coherency action initiated by the write. Therefore, the Completer is permitted to send a Comp as soon as receiving a WriteDataCancel response without dependency on either the processing of the write request or the completion of any snoops sent due to the write.

### B2.6.3 Completion acknowledgment

The relative ordering of transactions issued by a Requester, and Snoop transactions caused by transactions from different Requesters, is controlled by the use of a completion acknowledge, CompAck, response. This ensures that a Snoop transaction that is ordered after the transaction from the Requester is guaranteed to be received after the transaction response.

The sequencing of the completion of a Read transaction and the sending of CompAck is as follows:

1. An RN-F sends a CompAck after receiving Comp, RespSepData, or CompData, or both RespSepData and DataSepResp.
2. An HN-F, except in the case of ReadNoSnp and ReadOnce*, waits for CompAck before sending a subsequent snoop to the same address. For CopyBack transactions, WriteData acts as an implicit CompAck and an HN-F must wait for WriteData before sending a snoop to the same address.

This sequence guarantees that an RN-F receives completion for a transaction and a snoop to the same cache line in the same order as they are sent from an HN-F. This ensures transactions to the same cache line are observed in the correct order.

When an RN-F has a transaction in progress that uses CompAck, except for ReadNoSnp and ReadOnce*, a Snoop request is guaranteed to not be received to the same address between the point that Comp is received and the point that CompAck is sent.

For WriteNoSnp, WriteUnique, and their Combined Write variants, that require a CompAck message, a Request Node sends the CompAck after receiving the Comp, DBIDResp, or CompDBIDResp response.

The use of CompAck for a transaction is determined by the Requester setting the ExpCompAck field in the original request. The rules for a Request Node setting the ExpCompAck field and generating a CompAck response are as follows:

- An RN-F must include a CompAck response in all Read transactions except ReadNoSnp and ReadOnce*.
- An RN-F is permitted, but not required, to include a CompAck response in ReadNoSnp and ReadOnce* transactions.
- An RN-F must not include a CompAck response in StashOnce*, CMO, Atomic, or Evict transactions.
- An RN-I or RN-D is permitted, but not required, to include a CompAck response in Read transactions.
- An RN-I or RN-D must not include a CompAck response in Dataless or Atomic transactions.