| MemAttr[1] </br> Device[1] | MemAttr[3] </br> Allocate[3] | MemAttr[2] </br> Cacheable[2] | MemAttr[0] </br> EWA[0] | SnpAttr | LikelyShared | Order[1] | Order[0] | ARM Memory type                     |
|----------------------------|------------------------------|-------------------------------|-------------------------|---------|--------------|----------|----------|-------------------------------------|
| 1                          | All other values ᵇ                                                                                                                    | Not valid                           |
| 0                          | 0                            | 0                             | 0                       | 0       | 0            | 0/1 ᵃ    | 0        | Non-cacheable Non-bufferable ᶜ      |
| 0                          | 0                            | 0                             | 1                       | 0       | 0            | 0/1 ᵃ    | 0        | Non-cacheable Bufferable            |
| 0                          | 0                            | 1                             | 1                       | 0       | 0            | 0/1 ᵃ    | 0        | Non-snoopable WriteBack No-allocate |
| 0                          | 1                            | 1                             | 1                       | 0       | 0            | 0/1 ᵃ    | 0        | Non-snoopable WriteBack allocate    |
| 0                          | 0                            | 1                             | 1                       | 1       | 0/1 ᵈ        | 0/1 ᵃ    | 0        | Snoopable WriteBack No-allocate     |
| 0                          | 1                            | 1                             | 1                       | 1       | 0/1 ᵈ        | 0/1 ᵃ    | 0        | Snoopable WriteBack Allocate        |
| 0                          | All other values ᵇ                                                                                                                    | Not valid                           |

- ᵃ Order = 0b10 is permitted in ReadOnce*, WriteUnique, ReadNoSnp, WriteNoSnp, WriteNoSnpDef, and Atomic transactions only.
- ᵇ Order = 0b01 is not used for the ordering of transactions. See B2.6.5 Transaction ordering.
- ᶜ Non-cacheable Non-bufferable is an AXI memory type, not an ARM memory type.
- ᵈ See B2.7.5 Likely Shared.

#### B2.7.4.1 Memory type

This section specifies the required behavior for each of the memory types shown in Table B2.12.

##### B2.7.4.1.1 Device nRnE

The required behavior for Device nRnE memory type is:

- The write response must be obtained from the final destination.
- Read data must be obtained from the final destination.
- A read must not fetch more data than is required.
- A read must not be prefetched.
- Writes must not be merged.
- A write must not write to a larger address range than the original transaction.
- All Read and Write transactions from the same source to the same endpoint must remain ordered.

##### B2.7.4.1.2 Device nRE

The required behavior for the Device nRE memory type is the same as for the Device nRnE memory type, except that the write response can be obtained from an intermediate point.