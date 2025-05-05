Table B1.2 Continued from previous page

| Classification   | Supporting transactions   |
|------------------|---------------------------|
|                  | SnpOnce                   |
|                  | SnpStashUnique            |
|                  | SnpStashShared            |
|                  | SnpCleanFwd               |
|                  | SnpClean                  |
|                  | SnpNotSharedDirty         |
|                  | SnpSharedFwd              |
|                  | SnpShared                 |
|                  | SnpUniqueFwd              |
|                  | SnpUnique                 |
|                  | SnpPreferUniqueFwd        |
|                  | SnpPreferUnique           |
|                  | SnpUniqueStash            |
|                  | SnpCleanShared            |
|                  | SnpCleanInvalid           |
|                  | SnpMakeInvalid            |
|                  | SnpMakeInvalidStash       |
|                  | SnpQuery                  |

Table B1.3: Representation of transactions

| Specification use   | Represents collectively |
|---------------------|-------------------------|
| ReadOnce*           | ReadOnce, ReadOnceCleanInvalid, and ReadOnceMakeInvalid |
| WriteNoSnp          | WriteNoSnpPtl and WriteNoSnpFull |
| WriteUnique         | WriteUniquePtl, WriteUniqueFull, WriteUniquePtlStash, and WriteUniqueFullStash |
| WriteBack           | WriteBackPtl and WriteBackFull |
| StashOnce           | StashOnceUnique and StashOnceShared |
| StashOnceSep        | StashOnceSepUnique and StashOnceSepShared |
| StashOnce*          | StashOnce and StashOnceSep |
| StashOnce*Shared    | StashOnceShared and StashOnceSepShared |
| StashOnce*Unique    | StashOnceUnique and StashOnceSepUnique |

Continued on next page