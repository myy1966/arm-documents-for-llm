## B12.12 Requests and permitted tag operations

Table B12.3 shows a summary of the permitted TagOp field values in the different requests. The following key is used:

- Y Yes, permitted
- \- Not permitted

Table B12.3: Permitted TagOp values for each request type

| Requests              | Tag operation Invalid | Transfer | Update | Match | Fetch |
|-----------------------|-----------------------|----------|--------|-------|-------|
| ReadOnce              | Y                     | Y        | -      | -     | -     |
| ReadClean             | Y                     | Y        | -      | -     | -     |
| ReadShared            | Y                     | Y        | -      | -     | -     |
| ReadNotSharedDirty    | Y                     | Y        | -      | -     | -     |
| ReadPreferUnique      | Y                     | Y        | -      | -     | -     |
| ReadOnceMakeInvalid   | Y                     | Y        | -      | -     | -     |
| ReadOnceCleanInvalid  | Y                     | Y        | -      | -     | -     |
| ReadUnique            | Y                     | Y        | -      | -     | Y     |
| ReadNoSnp             | Y                     | Y        | -      | -     | Y     |
| ReadNoSnpSep          | Y                     | Y        | -      | -     | Y     |
| MakeReadUnique        | Y                     | Y        | -      | -     | -     |
| CleanShared           | Y                     | -        | -      | -     | -     |
| CleanSharedPersist    | Y                     | -        | -      | -     | -     |
| CleanSharedPersistSep | Y                     | -        | -      | -     | -     |
| CleanUnique           | Y                     | -        | -      | -     | -     |
| CleanInvalid          | Y                     | -        | -      | -     | -     |
| CleanInvalidPoPA      | Y                     | -        | -      | -     | -     |
| MakeInvalid           | Y                     | -        | -      | -     | -     |
| MakeUnique            | Y                     | -        | Y      | -     | -     |
| Evict                 | Y                     | -        | -      | -     | -     |
| StashOnceUnique       | Y                     | Y        | -      | -     | -     |
| StashOnceSepUnique    | Y                     | Y        | -      | -     | -     |
| StashOnceShared       | Y                     | Y        | -      | -     | -     |
| StashOnceSepShared    | Y                     | Y        | -      | -     | -     |
| WriteNoSnpFull        | Y                     | Y        | Y      | Y     | -     |
| WriteNoSnpDef         | Y                     | -        | -      | -     | -     |

Continued on next page