| subchapter                              | subsubchapter                                                       | page number |
|-----------------------------------------|---------------------------------------------------------------------|-------------|
|                                         | B2.2.3 Snoop request fields                                         | 47          |
|                                         | B2.2.4 Data fields                                                  | 49          |
| B2.3 Transaction structure              |                                                                     | 51          |
|                                         | B2.3.1 Read transactions                                            | 52          |
|                                         | B2.3.2 Write transactions                                           | 59          |
|                                         | B2.3.3 Atomic transactions                                          | 79          |
|                                         | B2.3.4 Stash transactions                                           | 81          |
|                                         | B2.3.5 Dataless transactions                                        | 84          |
|                                         | B2.3.6 Prefetch transactions                                        | 86          |
|                                         | B2.3.7 DVM transactions                                             | 87          |
|                                         | B2.3.8 Retry                                                        | 88          |
|                                         | B2.3.9 Home Initiated transactions                                  | 89          |
| B2.4 Transaction identifier fields      |                                                                     | 97          |
|                                         | B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID       | 97          |
|                                         | B2.4.2 Transaction Identifier, TxnID                                | 97          |
|                                         | B2.4.3 Data Buffer Identifier, DBID                                 | 98          |
|                                         | B2.4.4 Return Transaction Identifier, ReturnTxnID                   | 99          |
|                                         | B2.4.5 Forward Transaction Identifier, FwdTxnID                     | 100         |
|                                         | B2.4.6 Data Identifier, DataID, and Critical Chunk Identifier, CCID | 100         |
|                                         | B2.4.7 Logical Processor Identifier, LPID                           | 100         |
|                                         | B2.4.8 Stash Logical Processor Identifier, StashLPID                | 101         |
|                                         | B2.4.9 Stash Node Identifier, StashNID                              | 101         |
|                                         | B2.4.10 Return Node Identifier, ReturnNID                           | 101         |
|                                         | B2.4.11 Home Node Identifier, HomeNID                               | 102         |
|                                         | B2.4.12 Forward Node Identifier, FwdNID                             | 102         |
|                                         | B2.4.13 Persistence Group Identifier, PGroupID                      | 103         |
|                                         | B2.4.14 Stash Group Identifier, StashGroupID                        | 103         |
|                                         | B2.4.15 Tag Group Identifier, TagGroupID                            | 103         |
| B2.5 Transaction identifier field flows |                                                                     | 105         |
|                                         | B2.5.1 Read transactions                                            | 105         |
|                                         | B2.5.2 Dataless transactions                                        | 113         |
|                                         | B2.5.3 Write transactions                                           | 113         |
|                                         | B2.5.4 DVMOp transaction                                            | 125         |
|                                         | B2.5.5 Transaction requests with Retry                              | 125         |
|                                         | B2.5.6 Protocol Credit Return transaction                           | 126         |
| B2.6 Ordering                           |                                                                     | 127         |
|                                         | B2.6.1 Multi-copy atomicity                                         | 127         |
|                                         | B2.6.2 Completion response and ordering                             | 127         |
|                                         | B2.6.3 Completion acknowledgment                                    | 129         |
|                                         | B2.6.4 Ordering semantics of RespSepData and DataSepResp            | 131         |
|                                         | B2.6.5 Transaction ordering                                         | 132         |
| B2.7 Address, Control, and Data         |                                                                     | 139         |
|                                         | B2.7.1 Address                                                      | 139         |
|                                         | B2.7.2 Physical Address Space, PAS                                  | 139         |
|                                         | B2.7.3 Memory Attributes                                            | 140         |
|                                         | B2.7.4 Transaction attribute combinations                           | 143         |
|                                         | B2.7.5 Likely Shared                                                | 146         |
|                                         | B2.7.6 Snoop attribute                                              | 146         |
|                                         | B2.7.7 Mismatched Memory attributes                                 | 148         |
|                                         | B2.7.8 CopyAtHome attribute                                         | 150         |
| B2.8 Data transfer                      |                                                                     | 154         |
|                                         | B2.8.1 Data size                                                    | 154         |
|                                         | B2.8.2 Bytes access in memory                                       | 154         |
|                                         | B2.8.3 Byte Enables                                                 | 155         |
|                                         | B2.8.4 Data packetization                                           | 156         |