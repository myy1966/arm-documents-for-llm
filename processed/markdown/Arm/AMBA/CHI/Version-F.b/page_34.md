Table B1.2 Continued from previous page

| Classification   | Supporting transactions                              |
|------------------|------------------------------------------------------|
|                  | WriteUniqueZero                                      |
|                  | WriteUniquePtlStash                                  |
|                  | WriteUniqueFullStash                                 |
|                  | WriteBackPtl                                         |
|                  | WriteBackFull                                        |
|                  | WriteCleanFull                                       |
|                  | WriteEvictFull                                       |
|                  | WriteEvictOrEvict                                    |
| Combined Write   | WriteNoSnpPtlCleanInv                                |
|                  | WriteNoSnpPtlCleanSh                                 |
|                  | WriteNoSnpPtlCleanShPerSep                           |
|                  | WriteNoSnpPtlCleanInvPoPA                            |
|                  | WriteNoSnpFullCleanInv                               |
|                  | WriteNoSnpFullCleanSh                                |
|                  | WriteNoSnpFullCleanShPerSep                          |
|                  | WriteNoSnpFullCleanInvPoPA                           |
|                  | WriteUniquePtlCleanSh                                |
|                  | WriteUniquePtlCleanShPerSep                          |
|                  | WriteUniqueFullCleanSh                               |
|                  | WriteBackFullCleanInv                                |
|                  | WriteBackFullCleanShPerSep WriteBackFullCleanInvPoPA |
|                  | WriteCleanFullCleanSh                                |
|                  | WriteCleanFullCleanShPerSep                          |
| Atomic           | AtomicStore                                          |
|                  | AtomicLoad                                           |
|                  | AtomicSwap                                           |
|                  | AtomicCompare                                        |
| Other            | DVMOp                                                |
|                  | PrefetchTgt                                          |
|                  | PCrdReturn                                           |
| Snoop            | SnpOnceFwd                                           |

Continued on next page