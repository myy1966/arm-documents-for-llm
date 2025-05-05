Table C2.1 – Continued from previous page

<!-- MERGE table -->

| Request                      | From             | To Expected     | To Permitted |
|------------------------------|------------------|-----------------|--------------|
| ReadOnceMakeInvalid          |                  |                 |              |
| StashOnceUnique              |                  |                 |              |
| StashOnceShared              |                  |                 |              |
| StashOnceSepUnique           |                  |                 |              |
| StashOnceSepShared           |                  |                 |              |
| WriteUniqueFull              |                  |                 |              |
| WriteUniqueFullStash         |                  |                 |              |
| WriteUniquePtl               |                  |                 |              |
| WriteUniquePtlStash          |                  |                 |              |
| WriteUniqueZero              |                  |                 |              |
| CleanShared                  | RN-F, RN-D, RN-I | ICN(HN-F, HN-I) | -            |
| CleanSharedPersist           | ICN(HN-F)        | SN-F            | -            |
| CleanSharedPersistSep        | ICN(HN-I)        | SN-I            | -            |
| CleanInvalid                 |                  |                 |              |
| CleanInvalidPoPA             |                  |                 |              |
| MakeInvalid                  |                  |                 |              |
| WriteUniquePtlCleanSh        | RN-F, RN-D, RN-I | ICN(HN-F)       | ICN(HN-I)    |
| WriteUniquePtlCleanShPerSep  |                  |                 |              |
| WriteUniqueFullCleanSh       |                  |                 |              |
| WriteUniqueFullCleanShPerSep |                  |                 |              |
| WriteBackFullCleanInv        | RN-F             | ICN(HN-F)       | ICN(HN-I)    |
| WriteBackFullCleanInvPoPA    |                  |                 |              |
| WriteBackFullCleanSh         |                  |                 |              |
| WriteBackFullCleanShPerSep   |                  |                 |              |
| WriteCleanFullCleanSh        |                  |                 |              |
| WriteCleanFullCleanShPerSep  |                  |                 |              |
| WriteNoSnpFullCleanInv       | RN-F, RN-D, RN-I | ICN(HN-F, HN-I) | -            |
| WriteNoSnpFullCleanInvPoPA   | ICN(HN-F)        | SN-F            | -            |
| WriteNoSnpFullCleanSh        | ICN(HN-I)        | SN-I            | -            |
| WriteNoSnpFullCleanShPerSep  |                  |                 |              |
| WriteNoSnpPtlCleanInv        |                  |                 |              |
| WriteNoSnpPtlCleanInvPoPA    |                  |                 |              |
| WriteNoSnpPtlCleanSh         |                  |                 |              |

Continued on next page