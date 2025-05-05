Table C3.4 Continued from previous page

| Change                                                                                    | Location                                                   |
|-------------------------------------------------------------------------------------------|------------------------------------------------------------|
| CompCMO                                                                                   | B2.3.2.4 Combined Immediate Write and CMO                  |
| New feature: Two-part StashOnce transaction including:                                    | B2.3.4 Stash transactions                                  |
| StashOnceSep requests                                                                     | B2.5.3.4 StashOnce or StashOnceSep transaction             |
| StashDone response                                                                        | B4.2.2 Dataless transactions                               |
| CompStashDone response                                                                    | B7.3 Independent Stash request                             |
|                                                                                           | Chapter B9 Error Handling                                  |
|                                                                                           | Chapter B12 Memory Tagging                                 |
| New feature: Forward indication on Snoop forward treated as a hint                        | B4.4 Request transactions and corresponding Snoop requests |
| New feature: Increasing inter-port bandwidth                                              | B13.7 Increasing inter-port bandwidth                      |
| Multiple interfaces                                                                       |                                                            |
| Replicated channels                                                                       |                                                            |
| New feature: Memory tagging                                                               | Chapter B12 Memory Tagging                                 |
| New feature: Extending DVM operations:                                                    | Chapter B8 DVM Operations                                  |
| Range-based TLBI                                                                          |                                                            |
| Level hint in TLBI operation                                                              |                                                            |
| DVMDomain                                                                                 |                                                            |
| New feature: SLC Replacement Hint                                                         | B11.3 SLC Replacement Hint                                 |
| Additional requirement: Concerning Transcation Ordering guarantees                        | B2.6.5 Transaction ordering                                |
| Additional requirement: Concerning change in WriteNoSnpFull behavior                      | B2.3.2 Write transactions                                  |
| Correction: Concerning the Ordering guarantees provided by the Comp and CompData response | B2.6.2 Completion response and ordering                    |
| Update: Concerning removal of DoNotDataPull attribute on snoops                           | -                                                          |
| Update: Concerning extending the GroupID field width                                      | See Table C3.5 for further information                     |
| Update: Concerning extending the TxnID field width                                        | B13.9 Flit packet definitions                              |
| Update: Concerning ICache invalidation operations                                         | B8.4.5.2 Virtual Instruction Cache Invalidate              |
| Update: Concerning Secure EL2 TLBI operations                                             | B8.4.3 TLB Invalidate                                      |

Continued on next page