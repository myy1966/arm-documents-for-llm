Table B4.44: Cache state transitions at the Requester for Atomic request transactions

| Atomic request | Initial expected state | Initial permitted state | Final state | Comp response                       | WriteData response   |
|----------------|------------------------|-------------------------|-------------|-------------------------------------|----------------------|
| AtomicStore    | I, SC, UCE, SD         | UC, UD, UDP             | I           | DBIDResp* + Comp\_I or CompDBIDResp | NonCopyBackWriteData |
| AtomicLoad     | I, SC, UCE, SD         | UC, UD, UDP             | I           | DBIDResp* + CompData\_I             | NonCopyBackWriteData |
| AtomicSwap     | I, SC, UCE, SD         | UC, UD, UDP             | I           | DBIDResp* + CompData\_I             | NonCopyBackWriteData |
| AtomicCompare  | I, SC, UCE, SD         | UC, UD, UDP             | I           | DBIDResp* + CompData\_I             | NonCopyBackWriteData |

### B4.7.5 Other request transactions

DVMOp and PrefetchTgt requests do not have any cache state transitions associated with them.