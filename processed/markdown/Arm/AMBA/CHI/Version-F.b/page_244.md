Table B4.42 Continued from previous page

| Request type                          | Initial expected state | Initial permitted state | Final state | Comp response                         |
|---------------------------------------|------------------------|-------------------------|-------------|---------------------------------------|
| CleanShared, </br> CleanSharedPersist | I, SC, UC              | -                       | No Change   | Comp\_UC Comp\_SC                     |
| CleanShared, </br> CleanSharedPersist | I, SC, UC              | -                       | No Change   | Comp\_UC Comp\_UC                     |
| CleanShared, </br> CleanSharedPersist | I, SC, UC              | -                       | No Change   | Comp\_UC Comp\_I                      |
| CleanSharedPersistSep                 | I, SC, UC              | -                       | No Change   | Comp\_UC + Persist or CompPersist\_UC |
| CleanSharedPersistSep                 | I, SC, UC              | -                       | No Change   | Comp\_SC + Persist or CompPersist\_SC |
| CleanSharedPersistSep                 | I, SC, UC              | -                       | No Change   | Comp\_I + Persist or CompPersist\_I   |
| CleanInvalid </br> CleanInvalidPoPA   | I                      | -                       | I           | Comp\_I                               |
| MakeInvalid                           | I                      | -                       | I           | Comp\_I                               |

Before a CleanInvalid, CleanInvalidPoPA, MakeInvalid, or Evict transaction, it is permitted for the cache state to be UC, UCE or SC. However, it is required that the cache state transitions to the I state before the transaction is issued. Therefore, Table B4.42 shows I state as the only initial state.

### B4.7.3 Write request transactions

Table B4.43 shows the cache state transitions at the Requester, the WriteData response, and the combined or separate completion and DBIDResp response for Write and corresponding Combined Write request transactions. Combined Write request transactions are not listed in Table B4.43. See B4.2.4 Combined Write requests.

Table B4.43: Requester cache state transitions for Write request transactions

| Request type   | Initial state at Requester | State before WriteData or CompAck responses ᵃ | Final state | Comp response                    | WriteData or CompAck response                                          |
|----------------|----------------------------|-----------------------------------------------|-------------|----------------------------------|------------------------------------------------------------------------|
| WriteNoSnpPtl  | I                          | -                                             | I           | DBIDResp* + Comp or CompDBIDResp | NonCopyBackWriteData or NonCopyBackWriteDataCompAck or WriteDataCancel |
| WriteNoSnpFull | I                          | -                                             | I           | DBIDResp* + Comp or CompDBIDResp | NonCopyBackWriteData or NonCopyBackWriteDataCompAck                    |
| WriteNoSnpDef  | I                          | -                                             | I           | DBIDResp* + Comp or CompDBIDResp | NonCopyBackWriteData or WriteDataCancel                                |
| WriteNoSnpZero | I                          | -                                             | I           | DBIDResp* + Comp or CompDBIDResp | None                                                                   |

Continued on next page