- The Requester must send a CompAck response after receiving DBIDResp, DBIDRespOrd, CompDBIDResp, or Comp responses for the corresponding writes and Comp or CompDBIDResp responses for all earlier related ordered writes. If write data is to be sent, the Requester is permitted, but not required, to combine the CompAck response with the WriteData response into a NonCopyBackWriteDataCompAck response. When the Requester uses the combined CompAck and WriteData response for a transaction, a combined response must be sent for all WriteData transfers in that transaction. The method by which a Requester determines if a group of ordered writes are related is IMPLEMENTATION DEFINED.

> **_NOTE:_** Waiting to send CompAck response until all prior, related ordered writes have received their Comp responses ensures the operations at their respective HN-Fs have completed. Any Requester observing the write associated with the CompAck response also observes all prior, related ordered writes.

- The Requester that receives DBIDResp* and is ready to send CompAck must not wait for Comp to send CompAck.
- HN-F must wait for a CompAck response from the Request Node before deallocating a Write transaction and making the write visible to other observers.

##### B2.6.5.3.1 Optimized Streaming Ordered Write transactions

The writes in this section refer to WriteUnique or WriteNoSnp only. The Streaming Ordered Writes mechanism can be further optimized. If a previously sent write is to a different target, the Requester does not need to wait for the DBIDResp* for the request before sending the next ordered write. However, if the interconnect can remap the TgtID, the Requester must presume that all Write transactions are targeting the same HN-F and must not use the optimized version of the Streaming Ordered Writes flow.

An implementation using an optimized or non-optimized Streaming Ordered Writes solution must avoid deadlock and livelock situations.

> **_NOTE:_** A technique for avoiding resource-related deadlock or livelock issues is to limit Streaming Ordered Writes optimization to one Requester in the system. All other Requesters in the system can use the Streaming Ordered Writes solution without the optimization.
>
> In a typical system, the optimized Streaming Ordered Writes solution is most beneficial to an RN-I that is a conduit for PCIe style, non-relaxed order, Snoopable writes. In most systems, one RN-I hosting this type of PCIe traffic is adequate.
>
> OWOWrites can be used by more than one Requester by making use of WriteDataCancel messages to avoid resource related deadlocks and livelocks.

Figure B2.35 shows a typical transaction flow in which an RN-I uses Streaming Ordered WriteUnique transactions. This flow prevents a read acquiring the new value of Write-B before Write-A has completed.

> **_NOTE:_** For clarity, the Write-B DBIDResp* and the NCBWrData flow is omitted from Figure B2.35.