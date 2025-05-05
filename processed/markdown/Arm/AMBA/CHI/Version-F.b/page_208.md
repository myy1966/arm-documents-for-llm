Table B4.22: Request Node to Home Node Atomic request permitted attribute values

| Request                                       | Size (bytes) | SnoopMe | SnpAttr | MemAttr A C D E                                  | Order    | LikelyShared | ExpCompAck |
|-----------------------------------------------|--------------|---------|---------|--------------------------------------------------|----------|--------------|------------|
| AtomicStore </br> AtomicLoad </br> AtomicSwap | 1,2,4,8      | 0       | 0       | 0010                                             | 11       | 0            | 0          |
| AtomicStore </br> AtomicLoad </br> AtomicSwap | 1,2,4,8      | 0       | 0       | 0011                                             | 00,10,11 | 0            | 0          |
| AtomicStore </br> AtomicLoad </br> AtomicSwap | 1,2,4,8      | 0       | 0       | 0000 </br> 0001 </br> 0101 </br> 1101            | 00,10    | 0            | 0          |
| AtomicStore </br> AtomicLoad </br> AtomicSwap | 1,2,4,8      | 0,1     | 1       | 0101 </br> 1101                                  | 00,10    | 0            | 0          |
| AtomicCompare                                 | 2,4,8,16,32  | 0       | 0       | 0010                                             | 11       | 0            | 0          |
| AtomicCompare                                 | 2,4,8,16,32  | 0       | 0       | 0011 </br> 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10,11 | 0            | 0          |
| AtomicCompare                                 | 2,4,8,16,32  | 0       | 0       | 0011 </br> 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0            | 0          |
| AtomicCompare                                 | 2,4,8,16,32  | 0,1     | 1       | 0101 </br> 1101                                  | 00,10    | 0            | 0          |

Table B4.23: HN-F to SN-F Atomic request permitted attribute values

| Request                                      | Size (bytes) | SnoopMe | DoDWT | MemAttr A C D E                       | Order | LikelyShared | ExpCompAck |
|----------------------------------------------|--------------|---------|-------|---------------------------------------|-------|--------------|------------|
| AtomicStore </br> AtomicLoad </br> AtoicSwap | 1,2,4,8      | 0 ᵃ     | 0     | 0000 </br> 0001 </br> 0101 </br> 1101 | 00    | 0 ᵃ          | 0 ᵃ        |

Continued on next page