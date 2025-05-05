## B13.9 Flit packet definitions

This section defines the flit format. See:

- B13.9.1 Request flit
- B13.9.2 Response flit
- B13.9.3 Snoop flit
- B13.9.4 Data flit

### B13.9.1 Request flit

Table B13.6 shows the Request flit format in a REQ channel packet starting at bit 0.

The following key is used:

**MBZ** Must Be 0

Table B13.6: Request flit format

<!-- MERGE table -->

| REQFLIT[(R-1):0] format Field | Field width    | Comments                                   |
|-------------------------------|----------------|--------------------------------------------|
| QoS                           | 4              | -                                          |
| TgtID                         | 7 to 11        | Width determined by NodeID\_Width          |
| SrcID                         | 7 to 11        | Width determined by NodeID\_Width          |
| TxnID                         | 12             | -                                          |
| ReturnNID                     | 7 to 11        | Used for DMT                               |
| StashNID                      |                | Used in Stash transactions                 |
| {(NodeID\_Width - 7)' b0,     |                | MBZ                                        |
| SLCRepHint[6:0]}              |                | Used in cache line replacement algorithms  |
| StashNIDValid                 | 1              | Used in Stash transactions                 |
| Endian                        |                | Used in Atomic transactions                |
| Deep                          |                | Used in CleanSharedPersist* transactions   |
| ReturnTxnID[11:0]             | 12             | Used for DMT                               |
| {6' b0,                       |                | MBZ                                        |
| StashLPIDValid,               |                | Used in Stash transactions                 |
| StashLPID[4:0]}               |                | Used in Stash transactions                 |
| Opcode                        | 7              | -                                          |
| Size                          | 3              | -                                          |
| Addr                          | RAW = 44 to 52 | Width determined by Req\_Addr\_Width (RAW) |
| NS                            | 1              | -                                          |
| NSE                           | 1              | -                                          |
| LikelyShared                  | 1              | -                                          |

Continued on next page