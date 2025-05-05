- Must be asserted for the WriteEvictFull transaction.

> **_NOTE:_** A Requester can convert a WriteEvictFull with the Allocate bit not asserted to an Evict transaction.

- Must not be asserted for:

    - Device memory transactions.
    - Normal Non-cacheable memory transactions.

- Is inapplicable and:

    - Must be set to 0 in DVMOp, PCrdReturn, and Evict transactions.
    - Can take any value in the PrefetchTgt transaction.

#### B2.7.3.5 Propagation of Attr

A request from the Home Node to Subordinate Node sent in response to a request to the Home Node must preserve the MemAttr bits EWA, Device, Cacheable, and Allocate. The only exception to this rule is when the downstream memory is known to be Normal, then the Device field value can be set to 0b0 to indicate Normal.

In a Combined Write transaction, when the write and CMO transactions are separated, the Write transaction inherits the MemAttr and SnpAttr values of the original combined request. The separated CMO transaction SnpAttr and Cacheable bits must be set to the most pervasive to affect all caches at RN-F nodes and caches downstream.

For a ReadNoSnp or WriteNoSnp generated within the interconnect due to a Prefetch from Home or an eviction from the System cache:

- MemAttr bits EWA, Cacheable, and Allocate must all be set to 0b1.
- Device field value must be set to 0b0 to indicate Normal.
- SnpAttr field value must be set to 0b0 to indicate Non-snoopable.

### B2.7.4 Transaction attribute combinations

Table B2.12 lists the legal combinations of MemAttr, SnpAttr, and Order field values and the equivalent ARM memory type. The Order field is described in B2.6 Ordering.

Table B2.12: Legal combinations of MemAttr, SnpAttr, and Order field values

| MemAttr[1] </br> Device[1] | MemAttr[3] </br> Allocate[3] | MemAttr[2] </br> Cacheable[2] | MemAttr[0] </br> EWA[0] | SnpAttr | LikelyShared | Order[1] | Order[0] | ARM Memory type |
|----------------------------|------------------------------|-------------------------------|-------------------------|---------|--------------|----------|----------|-----------------|
| 1                          | 0                            | 0                             | 0                       | 0       | 0            | 1        | 1        | Device nRnE     |
| 1                          | 0                            | 0                             | 1                       | 0       | 0            | 1        | 1        | Device nRE      |
| 1                          | 0                            | 0                             | 1                       | 0       | 0            | 0/1 ᵃ    | 1        | Device RE       |

Continued on next page