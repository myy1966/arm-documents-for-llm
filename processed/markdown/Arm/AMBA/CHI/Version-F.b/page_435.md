Table B13.6 – Continued from previous page

<!-- MERGE table -->

| REQFLIT[(R-1):0] format Field | Field width                                             | Comments                             |
|-------------------------------|---------------------------------------------------------|--------------------------------------|
| AllowRetry                    | 1                                                       | -                                    |
| Order                         | 2                                                       | -                                    |
| PCrdType                      | 4                                                       | -                                    |
| MemAttr                       | 4                                                       | -                                    |
| SnpAttr                       | 1                                                       | -                                    |
| DoDWT                         |                                                         | Used for DWT                         |
| PGroupID[7:0]                 | 8                                                       | Used in PCMO transactions            |
| StashGroupID[7:0]             |                                                         | Used in the StashOnceSep transaction |
| TagGroupID[7:0]               |                                                         | Used for Memory Tagging              |
| {3' b0,                       |                                                         | MBZ                                  |
| LPID[4:0]}                    |                                                         | -                                    |
| Excl                          | 1                                                       | Used in Exclusive transactions       |
| SnoopMe                       |                                                         | Used in Atomic transactions          |
| CAH                           |                                                         | Used in CopyBack Write transactions  |
| ExpCompAck                    | 1                                                       | -                                    |
| TagOp                         | 2                                                       | -                                    |
| TraceTag                      | 1                                                       | -                                    |
| MPAM                          | M=0                                                     | No MPAM bus                          |
|                               | M=12                                                    | -                                    |
| PBHA                          | PB = 0                                                  | No PBHA bus                          |
|                               | PB = 4                                                  | -                                    |
| RSVDC                         | Y = 0                                                   | No RSVDC bus                         |
|                               | Y = 4, 8, 12, 16, 24, 32                                | -                                    |
| Total                         | R = (88 + RAW + Y + M + PB) to (100 + RAW + Y + M + PB) |                                      |

### B13.9.2 Response flit

Table B13.7 shows the Response flit format in a RSP channel packet starting at bit 0.

The following key is used:

**MBZ** Must Be Zero