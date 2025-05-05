## B4.11 Hazard conditions

This section lists the responsibilities of the RN-F and HN-F to handle address hazards and race conditions among Snoopable transactions. Ordering among Non-snoopable transactions and among Snoopable transactions is described in B2.6 Ordering.

In addition to many Requesters issuing transactions at the same time, the protocol also permits each Requester to make multiple outstanding requests, and to receive multiple outstanding snoop requests. The interconnect, that is, ICN(HN-F, HN-I and MN), is responsible to ensure that there is a defined order in which transactions to the same cache line can occur, and that the defined order is the same for all components.

### B4.11.1 At the RN-F node

An RN-F node must respond to received Snoop requests, except for SnpDVMOp(Sync), in a timely manner without creating any Protocol layer dependency on completion of outstanding requests.

If a pending request to the same cache line is present at the RN-F and the pending request has not received any response packets:

- The Snoop request must be processed normally.
- The cache state must transition as applicable for each Snoop request type.
- The cached data or CopyBack request data must be returned with the Snoop response, or forwarded to the Requester, if required by the Snoop request type, Snoop request attributes, and cache state.

If a pending request to the same cache line is present at the RN-F and the pending request has received at least one Data response packet or a RespSepData response:

- The RN-F must wait to receive all Data response packets before responding to the Snoop request.
- Once all the Data response packets are received by RN-F:

    - The Snoop request must be processed normally.
    - The cache state must transition as applicable for each Snoop request type.
    - The cached data must be returned with the Snoop response, or forwarded to the Requester, if required by the Snoop request type, Snoop request attributes, and cache state.

If the pending request is a CopyBack request, the following additional requirements apply:

- Request transaction flow must be completed after receiving the CompDBIDResp or Comp response.
- The cache state in the CopyBackWriteData or CompAck response must be the state of the cache line after the snoop request is processed, not the state at the time of sending the CopyBack request.
- If the cache line state is I after the Snoop response is sent, the cache state in the CopyBackWriteData or CompAck response must be I. Additionally, for a CopyBackWriteData response, all BE bits must be deasserted, and the corresponding data must be set to 0.
- If the cache line state is UC or SC after the Snoop response is sent, a Request Node is permitted to not send valid CopyBack Data. If the Request Node decides not to send valid CopyBack Data, the cache state in the CopyBackWriteData or CompAck response must be I. Additionally, for a CopyBackWriteData response, all BE bits must be deasserted, and the corresponding data must be set to 0.
- If data is included with CopyBackWriteData, it can be:

    - The same data that has been sent with the Snoop response.
    - More up to date data than sent with the snoop response. This is only possible when the snoop is SnpOnce, SnpOnceFwd, or SnpCleanShared, and the snoop response indicates the cache line can be further modified.