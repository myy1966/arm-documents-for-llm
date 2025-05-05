- No, not permitted

- n/a Not applicable

Table B2.13: Snoop attributes for different transaction types

| Transaction         | Non-snoopable | Snoopable |
|---------------------|---------------|-----------|
| ReadNoSnp           | Y             | -         |
| ReadNoSnpSep        | Y             | -         |
| ReadOnce*           | -             | Y         |
| ReadClean           | -             | Y         |
| ReadShared          | -             | Y         |
| ReadNotSharedDirty  | -             | Y         |
| ReadUnique          | -             | Y         |
| ReadPreferUnique    | -             | Y         |
| MakeReadUnique      | -             | Y         |
| CleanUnique         | -             | Y         |
| MakeUnique          | -             | Y         |
| StashOnce           | -             | Y         |
| CleanShared         | Y             | Y         |
| CleanSharedPersist* | Y             | Y         |
| CleanInvalid        | Y             | Y         |
| CleanInvalidPoPA    | Y             | Y         |
| MakeInvalid         | Y             | Y         |
| Evict               | -             | Y         |
| WriteNoSnp          | Y             | -         |
| WriteNoSnpDef       | Y             | -         |
| WriteBack           | -             | Y         |
| WriteClean          | -             | Y         |
| WriteEvictFull      | -             | Y         |
| WriteEvictOrEvict   | -             | Y         |
| WriteUnique         | -             | Y         |
| Atomic transactions | Y             | Y         |
| DVMOp               | n/a ᵃ         | n/a ᵃ     |
| PrefetchTgt         | n/a ᵇ         | n/a ᵇ     |

Continued on next page