The steps required to resolve this hazard are:

1. At Time C:

    - The SnpShared transaction ignores the hazard and reads the cache line data.
    - The cache line state is changed from UD to SC.

2. At Time D:

    - The CompDBIDResp for the CopyBack is sent to RN-F0.
    - RN-F0 sends back a CopyBackWriteData\_SC response.
    - The cache line state is changed from SC to I.

The data is clean for coherence and is not required to be sent to the interconnect for correct functionality. However, the protocol requires the CopyBack flow to be consistent irrespective of a snoop hazard. The cache line state in the WriteData response is SC because that is the state of the cache line when the WriteData response is sent.

> **_NOTE:_** The response to a Snoop request that hazards with an outstanding Evict must be SnpResp\_I.
>
> The only response that can be received for a CopyBack request, while a Snoop response to a Snoop request to the same address is pending, is a RetryAck. This includes data, if applicable.

Figure B5.26 shows a further example of a Snoop request hazarding with an outstanding CopyBack request. In this example, the Snoop request is a SnpOnce request generated as a result of a ReadOnce request from RN-F1. The SnpOnce request receives a copy of the data with the Snoop response but does not change the cache line state. In this case, the final data response from RN-F0 indicates that the data is Dirty and that HN-F must write the data back to memory.