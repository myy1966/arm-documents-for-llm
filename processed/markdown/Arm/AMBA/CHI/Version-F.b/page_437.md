Table B13.8 – Continued from previous page

<!-- MERGE table -->

| SNPFLIT[(S-1):0] format Field | Field width                          | Comments                          |
|-------------------------------|--------------------------------------|-----------------------------------|
| SrcID                         | 7 to 11                              | Width determined by NodeID\_Width |
| TxnID                         | 12                                   | -                                 |
| FwdNID                        | 7 to 11                              | Width determined by NodeID\_Width |
| {(NodeID\_Width - 4)' 0,      |                                      |                                   |
| PBHA[3:0]}                    |                                      |                                   |
| FwdTxnID[11:0]                | 12                                   | Used for DCT                      |
| {6' b0,                       |                                      | MBZ                               |
| StashLPIDValid,               |                                      | Used in Stash transactions        |
| StashLPID[4:0]}               |                                      | Used in Stash transactions        |
| {4' b0,                       |                                      | MBZ                               |
| VMIDExt[7:0]}                 |                                      | Used in DVM transactions          |
| Opcode                        | 5                                    | -                                 |
| Addr                          | SAW = 41 to 49                       | Req\_Addr\_Width - 3              |
| NS                            | 1                                    | -                                 |
| NSE                           | 1                                    | -                                 |
| DoNotGoToSD                   | 1                                    | -                                 |
| RetToSrc                      | 1                                    | -                                 |
| TraceTag                      | 1                                    | -                                 |
| MPAM                          | M=0                                  | No MPAM bus                       |
|                               | M=12                                 | -                                 |
| Total                         | S = (52 + SAW + M) to (60 + SAW + M) |                                   |

### B13.9.4 Data flit

Table B13.9 shows the Data flit format in a DAT channel packet starting at bit 0.

The number of data flits required is dependent on the number of data bytes, and the data bus width. See B2.8.4 Data packetization.

The data channel interface supports a 128-bit, 256-bit, and 512-bit data bus width. There are three data flit formats defined, one for each of the three data bus widths supported at the data channel interface.

DataCheck field width is either 0 or equal to the width of the Data field divided by 8.

Poison field width is either 0 or equal to the width of the Data field divided by 64.

The following key is used:

**MBZ** Must Be Zero