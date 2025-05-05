Table B2.6 – Continued from previous page

| Order[1:0] | ExpCompAck | DMT | DCT | Notes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------|------------|-----|-----|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 00         | 1          | Y   | Y   | When not using DMT, Home does not need to be notified of transaction completion. For DMT, to ensure that the request from the Home to the Subordinate Node is not given a RetryAck response: • When using ReadNoSnp to the Subordinate Node, Home must either obtain a ReadReceipt from the Subordinate Node or wait for the CompAck response from the Request Node. • When using ReadNoSnpSep to the Subordinate Node, Home must obtain a ReadReceipt from the Subordinate Node. Not permitted. For DCT, Home uses the SnpRespFwded or completion. |
| 01         | -          | -   | -   | Not permitted                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 10/11      | 0          | N   | Y   | SnpRespDataFwded snoop response to determine transaction                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 10/11      | 1          | Y   | Y   | For DMT, Home uses the CompAck response to determine transaction completion. For DCT, Home uses the SnpRespFwd or SnpRespDataFwded snoop response to determine transaction completion.                                                                                                                                                                                                                                                                                                                                                              |

For partial ReadNoSnp or ReadOnce\* transactions, that is, where the size is less than 64B:

    - The Home cannot use a DCT flow.
    - If a DMT flow is used to forward data directly from Subordinate to Requester, the Home must use a partial ReadNoSnp request to the Subordinate.
    - If the Home does not request a DMT flow, a full cache line or partial cache line ReadNoSnp can be used. The Home must only return the requested number of DAT packets to the Requester, regardless of the number of DAT packets it receives from the Subordinate. For more information, see B2.8.4 Data packetization.

### B2.3.2 Write transactions

Write transactions are grouped into the following types:

- B2.3.2.1 Immediate Write
- B2.3.2.2 Write Zero
- B2.3.2.3 CopyBack Write
- B2.3.2.4 Combined Immediate Write and CMO
- B2.3.2.5 Combined Immediate Write and Persist CMO
- B2.3.2.6 Combined CopyBack Write and CMO

#### B2.3.2.1 Immediate Write

Figure B2.3 shows the possible transaction flows for an Immediate Write transaction.