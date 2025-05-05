Table B4.25 Continued from previous page

| Request category | Request                                        | Expected Snoop                          |
|------------------|------------------------------------------------|-----------------------------------------|
| Read             | ReadShared                                     | SnpSharedFwd                            |
| Read             | ReadUnique                                     | SnpUniqueFwd                            |
| Read             | ReadPreferUnique                               | SnpPreferUniqueFwd                      |
| Read             | MakeReadUnique                                 | SnpCleanInvalid or SnpUniqueFwd ᵇ       |
| Dataless         | CleanUnique                                    | SnpCleanInvalid                         |
| Dataless         | MakeUnique                                     | SnpMakeInvalid                          |
| Dataless         | Evict                                          | None                                    |
| Dataless         | CleanShared                                    | SnpCleanShared                          |
| Dataless         | CleanSharedPersist </br> CleanSharedPersistSep | SnpCleanShared                          |
| Dataless         | CleanInvalid </br> CleanInvalidPoPA            | SnpCleanInvalid                         |
| Dataless         | MakeInvalid                                    | SnpMakeInvalid                          |
| Dataless-stash   | StashOnceUnique </br> StashOnceSepUnique       | SnpStashUnique                          |
| Dataless-stash   | StashOnceShared </br> StashOnceSepShared       | SnpStashShared                          |
| Write            | WriteNoSnp                                     | None                                    |
| Write            | WriteNoSnpDef                                  | None                                    |
| Write            | WriteUniqueFull                                | SnpMakeInvalid                          |
| Write            | WriteUniquePtl                                 | SnpCleanInvalid or SnpUnique            |
| Write            | WriteUniqueZero                                | SnpMakeInvalid                          |
| Write-stash      | WriteUniqueFullStash                           | SnpMakeInvalidStash                     |
| Write-stash      | WriteUniquePtlStash                            | SnpUniqueStash or SnpMakeInvalidStash ᶜ |
| Write-CopyBack   | WriteBack                                      | None                                    |
| Write-CopyBack   | WriteClean                                     | None                                    |
| Write-CopyBack   | WriteEvictFull                                 | None                                    |
| Write-CopyBack   | WriteEvictOrEvict                              | None                                    |
| Atomic           | AtomicStore                                    | SnpUnique                               |
| Atomic           | AtomicLoad                                     | SnpUnique                               |
| Atomic           | AtomicSwap                                     | SnpUnique                               |
| Atomic           | AtomicCompare                                  | SnpUnique                               |

Continued on next page