## C2.1 Request communicating nodes

Table C2.1 shows the Request communicating nodes. In Table C2.1, unless explicitly stated otherwise, a reference to a Write transaction includes both the individual Write transaction and the corresponding Combined Write transaction.

For some Requests, both an expected target and a permitted target are given. The use of the permitted target can occur in the case of a software based error. The permitted target must complete the transaction in a protocol compliant manner, this might require the use of an error response.

Table C2.1: Request communicating nodes

<!-- MERGE table -->

| Request              | From             | To Expected     | To Permitted |
|----------------------|------------------|-----------------|--------------|
| ReadNoSnp            | RN-F, RN-D, RN-I | ICN(HN-F, HN-I) | -            |
| WriteNoSnpPtl        | ICN(HN-F)        | SN-F            | -            |
| WriteNoSnpFull       | ICN(HN-I)        | SN-I            | -            |
| WriteNoSnpZero       |                  |                 |              |
| WriteNoSnpDef        | RN-F             | HN-I            | HN-F         |
|                      | RN-D, RN-I ᵃ     |                 |              |
|                      | ICN(HN-I)        | SN-I            | -            |
| ReadNoSnpSep         | ICN(HN-F)        | SN-F            | -            |
|                      | ICN(HN-I)        | SN-I            | -            |
| ReadClean            | RN-F             | ICN(HN-F)       | ICN(HN-I)    |
| ReadShared           |                  |                 |              |
| ReadNotSharedDirty   |                  |                 |              |
| ReadUnique           |                  |                 |              |
| MakeReadUnique       |                  |                 |              |
| CleanUnique          |                  |                 |              |
| MakeUnique           |                  |                 |              |
| Evict                |                  |                 |              |
| WriteBackPtl         |                  |                 |              |
| WriteBackFull        |                  |                 |              |
| WriteCleanFull       |                  |                 |              |
| WriteEvictFull       |                  |                 |              |
| WriteEvictOrEvict    |                  |                 |              |
| ReadOnce             | RN-F, RN-D, RN-I | ICN(HN-F)       | ICN(HN-I)    |
| ReadOnceCleanInvalid |                  |                 |              |

Continued on next page