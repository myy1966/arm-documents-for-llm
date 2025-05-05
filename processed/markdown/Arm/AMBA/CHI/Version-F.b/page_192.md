Table B4.7 – Continued from previous page

| Request                                                                                                                      | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                                             | Order | LikelyShared | ExpCompAck |
|------------------------------------------------------------------------------------------------------------------------------|--------------|------|---------|-------------------------------------------------------------|-------|--------------|------------|
| Evict                                                                                                                        | 64           | 0    | 1       | 0101                                                        | 00    | 0            | 0          |
| StashOnceUnique </br> StashOnceSepUnique </br> StashOnceShared </br> StashOnceSepShared                                      | 64           | 0    | 1       | 0101 </br> 1101                                             | 00    | 0,1          | 1          |
| CleanShared </br> CleanSharedPersist </br> CleanSharedPersistSep </br> CleanInvalid </br> CleanInvalidPoPA </br> MakeInvalid | 64           | 0    | 1       | 0101 </br> 1101                                             | 00 ᵃ  | 0            | 0          |
| CleanShared </br> CleanSharedPersist </br> CleanSharedPersistSep </br> CleanInvalid </br> CleanInvalidPoPA </br> MakeInvalid | 64           | 0    | 0       | 0010 </br> 0011 </br> 0000 </br> 0001 </br> 0101 </br> 1101 | 00 ᵃ  | 0            | 0          |

- ᵃ This field is inapplicable and must be set to 0.

Table B4.8: HN-F to SN-F Dataless request permitted attribute values

| Request                                                                                                                      | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                       | Order | LikelyShared | ExpCompAck |
|------------------------------------------------------------------------------------------------------------------------------|--------------|------|---------|---------------------------------------|-------|--------------|------------|
| CleanShared </br> CleanSharedPersist </br> CleanSharedPersistSep </br> CleanInvalid </br> CleanInvalidPoPA </br> MakeInvalid | 64           | 0    | 0       | 0000 </br> 0001 </br> 0101 </br> 1101 | 00 ᵃ  | 0            | 0          |

- ᵃ This field is inapplicable and must be set to 0.

Table B4.9 lists the values permitted for key attributes in Dataless requests from HN-I to SN-I.