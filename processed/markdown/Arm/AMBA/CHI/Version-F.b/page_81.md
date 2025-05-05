    - The Requester sends write data, NonCopyBackWriteData, to the Home. The Requester must only send this after receiving DBIDResp, DBIDRespOrd, or CompDBIDResp.
    - Optionally, when the request requires a TagMatch response, the Home returns a tag match response, TagMatch, to the Requester. It is permitted, but not required, to wait for write data before returning TagMatch.

2. **Other Atomic transactions**

    For an AtomicLoad, AtomicSwap, or AtomicCompare transaction:

    - The Requester sends an AtomicLoad, AtomicSwap, or AtomicCompare request to the Home.
    - The Home sends a data request response, DBIDResp or DBIDRespOrd, to the Requester.
    - The Requester sends write data, NonCopyBackWriteData, to the Home. The Requester must only send this after receiving DBIDResp or DBIDRespOrd. The Requester must not wait to receive CompData before write data is sent.
    - The Home returns a combined data and completion response, CompData, to the Requester. It is permitted, but not required, to wait for write data before returning CompData.
    - Optionally, when the request requires a TagMatch response, the Home returns a tag match response, TagMatch, to the Requester. It is permitted, but not required, to wait for write data before returning TagMatch.

### B2.3.4 Stash transactions

Figure B2.10 shows the possible transaction flows for stash transactions.