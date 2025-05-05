Table C2.1 Continued from previous page

<!-- MERGE table -->

| Request                    | From             | To Expected         | To Permitted |
|----------------------------|------------------|---------------------|--------------|
| WriteNoSnpPtlCleanShPerSep |                  |                     |              |
| DVMOp                      | RN-F             | ICN(MN)             | -            |
| PCrdReturn                 | RN-F, RN-D, RN-I | ICN(HN-F, HN-I, MN) | -            |
|                            | ICN(HN-F)        | SN-F                | -            |
|                            | ICN(HN-I)        | SN-I                | -            |
| AtomicStore                | RN-F, RN-D, RN-I | ICN(HN-F, HN-I)     | -            |
| AtomicLoad                 | ICN(HN-F)        | SN-F                | -            |
| AtomicSwap                 | ICN(HN-I)        | SN-I                | -            |
| AtomicCompare              |                  |                     |              |
| PrefetchTgt                | RN-F, RN-D, RN-I | SN-F                | -            |

- ᵃ The request is permitted, but not expected, from RN-D or RN-I