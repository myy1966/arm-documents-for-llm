## B1.4 Transaction classification

The protocol transactions that this specification supports, and their major classification, are listed in Table B1.2.

Table B1.2: Transaction classification

| Classification   | Supporting transactions   |
|------------------|---------------------------|
| Read             | ReadNoSnp                 |
|                  | ReadNoSnpSep              |
|                  | ReadOnce                  |
|                  | ReadOnceCleanInvalid      |
|                  | ReadOnceMakeInvalid       |
|                  | ReadClean                 |
|                  | ReadNotSharedDirty        |
|                  | ReadShared                |
|                  | ReadUnique                |
|                  | ReadPreferUnique          |
|                  | MakeReadUnique            |
| Dataless         | CleanUnique               |
|                  | MakeUnique                |
|                  | Evict                     |
|                  | StashOnceUnique           |
|                  | StashOnceSepUnique        |
|                  | StashOnceShared           |
|                  | StashOnceSepShared        |
|                  | CleanShared               |
|                  | CleanSharedPersist        |
|                  | CleanSharedPersistSep     |
|                  | CleanInvalid              |
|                  | CleanInvalidPoPA          |
|                  | MakeInvalid               |
| Write            | WriteNoSnpPtl             |
|                  | WriteNoSnpFull            |
|                  | WriteNoSnpZero            |
|                  | WriteNoSnpDef             |
|                  | WriteUniquePtl            |
|                  | WriteUniqueFull           |

Continued on next page