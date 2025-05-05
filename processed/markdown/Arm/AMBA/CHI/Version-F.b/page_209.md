Table B4.23 – Continued from previous page

| Request       | Size (bytes) | SnoopMe | DoDWT | MemAttr A C D E                       | Order |  | ExpCompAck |
|---------------|--------------|---------|-------|---------------------------------------|-------|--------------|------------|
| AtomicCompare | 2,4,8,16,32  | 0 ᵃ     | 0     | 0000 </br> 0001 </br> 0101 </br> 1101 | 00    | 0 ᵃ          | 0 ᵃ        |

- ᵃ The field is inapplicable and must be set to 0.

Table B4.24: HN-I to SN-I Atomic request permitted attribute values

| Request                                       | Size (bytes) | SnoopMe | DoDWT | MemAttr A C D E                       | Order    | LikelyShared | ExpCompAck |
|-----------------------------------------------|--------------|---------|-------|---------------------------------------|----------|--------------|------------|
| AtomicStore </br> AtomicLoad </br> AtomicSwap | 1,2,4,8      | 0 ᵃ     | 0     | 0010                                  | 11       | 0 ᵃ          | 0 ᵃ        |
| AtomicStore </br> AtomicLoad </br> AtomicSwap | 1,2,4,8      | 0 ᵃ     | 0     | 0011                                  | 00,10,11 | 0 ᵃ          | 0 ᵃ        |
| AtomicStore </br> AtomicLoad </br> AtomicSwap | 1,2,4,8      | 0 ᵃ     | 0     | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0 ᵃ          | 0 ᵃ        |
Continued on next page