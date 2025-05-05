    - Older data than was sent with the snoop response. This is only possible when the CopyBack write is a WriteClean, the snoop request is SnpOnce*, and the response indicates that the cache line can be further modified.

For non-ordered transactions, the Request Node can send CompAck without waiting for DataSepResp. For ordered transactions, the Request Node can send CompAck as soon as the first packet of DataSepResp is received. In both cases, a Request Node must not respond to a Snoop request before receiving all data packets.

The RN-F could receive multiple snoop requests before a response is received for a pending CopyBack request for the same cache line. In this instance, the data response carries the cache line state after the completion of the response to the last snoop request. Such a scenario is possible because the CopyBack request can be queued behind multiple Read and Dataless requests at the HN-F.

### B4.11.2 At the ICN(HN-F) node

An HN-F orders transactions to the same cache line by sequencing transaction responses and Snoop transactions to the Requesters. As the interconnect is not required to be ordered, the arrival order of these messages, in certain cases, could not be the same as the order in which they were issued at the HN-F.

If a Response message that includes data requires multiple packets or beats of transfers over the interconnect, receiving or sending the message by Home implies sending or receiving all the packets corresponding to that message. That is, when a Home starts sending the message, all packets of the message must be sent without dependence on completion of any other request or response message.

Similarly, when a Home accepts part of the Data message, the remaining packets of that message must be accepted without any dependence on forward progress of any other request or response message.

When a subsequent forwarding of data depends upon receiving a Data message, the forwarding of data action can occur after receiving the first Data packet. A subsequent Non-data forwarding action that is processing of a subsequent request at Home as a consequence of sending or receiving of data by Home, must wait until all data is sent or received.

While a Snoop transaction response is pending, the only transaction responses that are permitted to be sent to the same address are:

- RetryAck for a CopyBack
- RetryAck and DBIDResp for a WriteUnique and Atomics
- RetryAck and, if applicable, a ReadReceipt for a Read request type
- RetryAck for a Dataless request type

Once a completion is sent for a transaction, the HN-F must not send a Snoop request to the same cache line until receiving:

- A CompAck for any Read and Dataless requests except for ReadOnce* and ReadNoSnp.
- A CompAck response for a CopyBack request that the HN-F has requested completes without a data transfer.
- A CopyBackWriteData response for a CopyBack request that the HN-F has requested completes with a data transfer.
- A NonCopyBackWriteData response for an Atomic request.
- A WriteData response, and if applicable, CompAck, for a WriteUnique request where the HN-F has not used a DWT flow.
- A Comp response from the Subordinate Node for a WriteUnique request where the HN-F has used a DWT flow.