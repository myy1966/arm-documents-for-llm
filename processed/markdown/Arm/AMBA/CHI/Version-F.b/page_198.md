Table B4.14 Continued from previous page

| Request                                    | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                       | Order    | LikelyShared | ExpCompAck |
|--------------------------------------------|--------------|------|---------|---------------------------------------|----------|--------------|------------|
| WriteNoSnpDef                              | 64           | 0    | 0       | 0010                                  | 11       | 0            | 0          |
| WriteNoSnpDef                              |              |      |         | 0011                                  | 00,10,11 | 0            | 0          |
| WriteNoSnpDef                              |              |      |         | 0000 </br> 0001                       | 00,10    | 0            | 0          |
| WriteNoSnpZero                             | 64           | 0    | 0       | 0010                                  | 11       | 0            | 0          |
| WriteNoSnpZero                             |              |      |         | 0011                                  | 00,10,11 | 0            | 0          |
| WriteNoSnpZero                             |              |      |         | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0            | 0          |
| WriteUniqueFull </br> WriteUniqueFullStash | 64           | 0    | 1       | 0101 </br> 1101                       | 00       | 0,1          | 0          |
| WriteUniqueFull </br> WriteUniqueFullStash | 64           | 0    | 1       | 0101 </br> 1101                       | 10       | 0,1          | 0,1        |
| WriteUniquePtl </br> WriteUniquePtlStash   | <=64         | 0    | 1       | 0101 </br> 1101                       | 00       | 0,1          | 0          |
| WriteUniquePtl </br> WriteUniquePtlStash   | <=64         | 0    | 1       | 0101 </br> 1101                       | 10       | 0,1          | 0,1        |
| WriteUniqueZero                            | 64           | 0    | 1       | 0101 </br> 1101                       | 00,10    | 0,1          | 0          |
| WriteBackFull </br> WriteCleanFull         | 64           | 0    | 1       | 0101 </br> 1101                       | 00       | 0,1          | 0          |
| WriteBackPtl                               | 64           | 0    | 1       | 0101 </br> 1101                       | 00       | 0            | 0          |
| WriteEvictFull                             | 64           | 0    | 1       | 1101                                  | 00       | 0,1          | 0          |
| WriteEvictOrEvict                          | 64           | 0    | 1       | 1101                                  | 00       | 0,1          | 1          |
