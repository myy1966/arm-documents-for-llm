Table B12.3 Continued from previous page

| Requests                 | Tag operation Invalid | Transfer | Update | Match | Fetch |
|--------------------------|-----------------------|----------|--------|-------|-------|
| WriteUniqueFull          | Y                     | -        | Y      | Y     | -     |
| WriteUniqueFullStash     | Y                     | -        | Y      | Y     | -     |
| WriteNoSnpPtl            | Y                     | -        | Y      | Y     | -     |
| WriteUniquePtl           | Y                     | -        | Y      | Y     | -     |
| WriteUniquePtlStash      | Y                     | -        | Y      | Y     | -     |
| WriteBackFull            | Y                     | Y        | Y      | -     | -     |
| WriteCleanFull           | Y                     | Y        | Y      | -     | -     |
| WriteBackPtl             | Y                     | -        | -      | -     | -     |
| WriteEvictFull           | Y                     | Y        | -      | -     | -     |
| WriteEvictOrEvict        | Y                     | Y        | -      | -     | -     |
| WriteNoSnpFull + (P)CMO  | Y                     | Y        | Y      | -     | -     |
| WriteNoSnpPtl + (P)CMO   | Y                     | -        | Y      | -     | -     |
| WriteUniqueFull + (P)CMO | Y                     | -        | -      | -     | -     |
| WriteUniquePtl + (P)CMO  | Y                     | -        | -      | -     | -     |
| WriteBackFull + (P)CMO   | Y                     | Y        | Y      | -     | -     |
| WriteCleanFull + (P)CMO  | Y                     | Y        | Y      | -     | -     |
| WriteNoSnpZero           | Y                     | -        | -      | -     | -     |
| WriteUniqueZero          | Y                     | -        | -      | -     | -     |
| Atomic*                  | Y                     | -        | -      | Y     | -     |
| PrefetchTgt              | Y                     | Y        | -      | -     | -     |
| PCrdReturn               | Y                     | -        | -      | -     | -     |
| DVMOp                    | Y                     | -        | -      | -     | -     |

The TagOp field in ReqLCrdReturn, DatLCrdReturn, and RspLCrdReturn is inapplicable and can take any value.

The Tag and TU fields in DatLCrdReturn are inapplicable and can take any value.