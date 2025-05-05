    - The hazard detection results in the WriteBack being blocked.
    - The ReadShared transaction receives data with the snoop response and must update memory in addition to sending the data to the Requester.

2. At Time B:

    - The WriteBack is unblocked because the HN-F has sent the data response to the Requester and a WriteData response to memory for the ReadShared transaction.

If the ReadShared request reaches the HN-F, after the HN-F has started processing the WriteBack request, the ReadShared request is blocked until completion of the WriteBack request.

A CopyBack request is completed at HN-F when both of the following are true:

- A data message corresponding to the CopyBack request is received.
- A memory update is completed if necessary.

### B5.6.4 Race hazard

After completion, a request could silently evict the cache line from the cache and generate another request to the same address. For example:

1. The regenerated request reaches the HN-F before the CompAck response associated with the earlier request.
2. The HN-F detects an address hazard and blocks the processing of the new request until the CompAck response is received.

In such a scenario, on arrival at HN-F, the CompAck response deallocates the previous request from the HN-F and unblocks the processing of the new request.