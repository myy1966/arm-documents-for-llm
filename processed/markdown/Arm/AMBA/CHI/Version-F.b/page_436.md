Table B13.7: Response flit format

<!-- MERGE table -->

| RSPFLIT[(T-1):0] format Field | Field width  | Comments                            |
|-------------------------------|--------------|-------------------------------------|
| QoS                           | 4            | -                                   |
| TgtID                         | 7 to 11      | Width determined by NodeID\_Width   |
| SrcID                         | 7 to 11      | Width determined by NodeID\_Width   |
| TxnID                         | 12           | -                                   |
| Opcode                        | 5            | -                                   |
| RespErr                       | 2            | -                                   |
| Resp                          | 3            | -                                   |
| FwdState[2:0]                 | 3            | Used for DCT                        |
| DataPull[2:0]                 |              | Used in Stash transactions          |
| CBusy                         | 3            | -                                   |
| DBID[11:0]                    | 12           | -                                   |
| {4' b0,                       |              | MBZ                                 |
| PGroupID[7:0]}                |              | Used in Persistent CMO transactions |
| {4' b0,                       |              | MBZ                                 |
| StashGroupID[7:0]}            |              | Used in Stash transactions          |
| {4' b0,                       |              | MBZ                                 |
| TagGroupID[7:0]}              |              | Used for Memory Tagging             |
| PCrdType                      | 4            | -                                   |
| TagOp                         | 2            | -                                   |
| TraceTag                      | 1            | -                                   |
| Total                         | T = 65 to 73 | T = 65 to 73                        |

### B13.9.3 Snoop flit

Table B13.8 shows the Snoop flit format in a SNP channel packet starting at bit 0.

The following key is used:

**MBZ** Must Be Zero

Table B13.8: Snoop flit format

<!-- MERGE table -->

| SNPFLIT[(S-1):0] format Field | Field width | Comments |
|-------------------------------|-------------|----------|
| QoS                           | 4           | -        |

Continued on next page