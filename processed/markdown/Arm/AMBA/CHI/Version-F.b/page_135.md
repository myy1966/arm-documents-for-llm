4. The Home Node cannot immediately accept the ReadNoSnp-2 request and returns the RetryAck-2 response to the Request Node.
5. The Request Node must now wait for a PCrdGrant to be sent from the Home Node before resending the ReadNoSnp-2 request. The Request Node does not send ReadNoSnp-3 at this point, to order ReadNoSnp-3 behind ReadNoSnp-2. This ordering requires that ReadNoSnp-2 must be accepted at the Home Node before ReadNoSnp-3 is sent to the Home Node.
6. After receipt of an appropriate PCrdGrant, the Request Node resends the ReadNoSnp-2 request.
7. The Home Node accepts the request and returns a ReadReceipt-2 response to the Request Node.
8. After receipt of the ReadReceipt-2 response, the Request Node sends the ReadNoSnp-3 request to the Home Node.
9. The Home Node accepts the request and returns the ReadReceipt-3 response to the Request Node.
10. Each of the read transactions is completed with the Requester receiving a completion and data. This is not shown in Figure B2.34.

> **_NOTE:_** Figure B2.34 shows a single ordered stream of three reads from the Request Node. However, a Request Node can have multiple streams of reads, so requests must be ordered within a stream. However, ordering dependency does not exist between streams. For example, when the streams are from different threads within the Request Node. In this case, the Request Node waits for the ReadReceipt of the previous request from the same thread only before sending out the next ordered request from that stream.

#### B2.6.5.2 CopyBack Request order

An RN-F must wait for the CompDBIDResp or Comp response to be received for an outstanding CopyBack transaction before issuing another request to the same cache line.

- It is permitted for an Atomic transaction with SnoopMe asserted to be issued before the CompDBIDResp or Comp response is received for an outstanding CopyBack to the same cache line.
- It is permitted for a CopyBack transaction to be issued before the CompDBDResp or Comp response is received for an outstandng Atomic transaction, with SnoopMe asserted, to the same cache line.

#### B2.6.5.3 Streaming Ordered Write transactions

The architectural mechanisms applicable to increasing Ordered Write Observation (OWO) Write streaming efficiency, and the corresponding constraints, are applicable to WriteUnique and WriteNoSnp transactions only.

If a Requester requires a sequence of Write transactions to be observed in the same order as they are issued, the Requester can wait for completion for a write before issuing the next write in the sequence. Such an observation ordering is typically termed OWO. This specification provides a mechanism termed Streaming Ordered Writes to more efficiently stream such ordered Write transactions.

The Streaming Ordered Write mechanism relies on the use of the OWO ordering requirement and CompAck. Responsibilities of Requesters and HN-F when utilizing the Streaming Ordered Write solution are:

- The Requester must set the Order field to 0b10 and set ExpCompAck on the Write request.
- The OWO requirement in a Write request indicates to the HN-F that the completion of coherence action on this write must not depend on completion of coherence action on a subsequent write.
- The Requester must wait for DBIDResp, DBIDRespOrd, CompDBIDResp, or Comp for a Write transaction before sending the next Write request.