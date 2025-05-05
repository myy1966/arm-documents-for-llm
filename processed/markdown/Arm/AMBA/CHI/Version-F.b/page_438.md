Table B13.9: Data flit fields

<!-- MERGE table -->

| DATFLIT[(D-1):0] format Field | Field width              | Comments                            |
|-------------------------------|--------------------------|-------------------------------------|
| QoS                           | 4                        | -                                   |
| TgtID                         | 7 to 11                  | Width determined by NodeID\_Width   |
| SrcID                         | 7 to 11                  | Width determined by NodeID\_Width   |
| TxnID                         | 12                       | -                                   |
| HomeNID                       | 7 to 11                  | Width determined by NodeID\_Width   |
| {(NodeID\_Width - 4)' b0,     |                          |                                     |
| PBHA[3:0]}                    |                          |                                     |
| Opcode                        | 4                        | -                                   |
| RespErr                       | 2                        | -                                   |
| Resp                          | 3                        | -                                   |
| DataSource[4:0]               | 5                        | Indicates Data source in a response |
| {2' b0,                       |                          | MBZ                                 |
| FwdState[2:0]}                |                          | Used for DCT                        |
| {2' bX,                       |                          | Can take any value                  |
| DataPull[2:0]}                |                          | Used in Stash transactions          |
| CBusy                         | 3                        | -                                   |
| DBID[11:0]                    | 12                       | -                                   |
| CCID                          | 2                        | -                                   |
| DataID                        | 2                        | -                                   |
| TagOp                         | 2                        | -                                   |
| Tag                           | DW/32 = 4, 8, 16         | -                                   |
| TU                            | DW/128 = 1, 2, 4         | -                                   |
| TraceTag                      | 1                        | -                                   |
| CAH                           | 1                        | -                                   |
| RSVDC                         | Y = 0                    | No RSVDC bus                        |
|                               | Y = 4, 8, 12, 16, 24, 32 | -                                   |
| BE                            | DW/8 = 16, 32, 64        | -                                   |
| Data                          | DW=128, 256, 512         | DW=B16.1.13 Data\_Width             |
| DataCheck                     | 0 or DW/8 = 16, 32, 64   | DC = DataCheck                      |

Continued on next page