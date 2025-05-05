Table B4.9: HN-I to SN-I Dataless request permitted attribute values

| Request                                                                                                                      | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                                             | Order | LikelyShared | ExpCompAck |
|------------------------------------------------------------------------------------------------------------------------------|--------------|------|---------|-------------------------------------------------------------|-------|--------------|------------|
| CleanShared </br> CleanSharedPersist </br> CleanSharedPersistSep </br> CleanInvalid </br> CleanInvalidPoPA </br> MakeInvalid | 64           | 0    | 0       | 0010 </br> 0011 </br> 0011 </br> 0001 </br> 0101 </br> 1101 | 00 ᵃ  | 0            | 0          |

- ᵃ This field is inapplicable and must be set to 0.

#### B4.2.2.4 Initial cache state at the Requester

Table B4.10 lists the permitted Requester cache states when a request is sent. The following key is used for Table B4.10, Table B4.11 and Table B4.12:

- Y Yes, permitted
- \- Not permitted

Table B4.10: Permitted Requester cache state at the sending of Dataless request

| Request               | Initial state <br> UD | Initial state <br> UC | Initial state <br> SD | Initial state <br> SC | Initial state <br> I | Initial state <br> UDP | Initial state <br> UCE |
|-----------------------|-----------------------|-----------------------|-----------------------|-----------------------|----------------------|------------------------|------------------------|
| CleanUnique           | Y                     | Y                     | Y                     | Y                     | Y                    | -                      | Y                      |
| MakeUnique            | -                     | Y                     | Y                     | Y                     | Y                    | -                      | Y                      |
| Evict                 | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |
| StashOnceUnique       | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |
| StashOnceSepUnique    | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |
| StashOnceShared       | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |
| StashOnceSepShared    | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |
| CleanShared           | -                     | Y                     | -                     | Y                     | Y                    | -                      | -                      |
| CleanSharedPersist    | -                     | Y                     | -                     | Y                     | Y                    | -                      | -                      |
| CleanSharedPersistSep | -                     | Y                     | -                     | Y                     | Y                    | -                      | -                      |

Continued on next page