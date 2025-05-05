## Chapter B13 Link Layer

| subchapter                            | subsubchapter                                                      | page number |
|---------------------------------------|--------------------------------------------------------------------|-------------|
| B13.1 Introduction                    |                                                                    | 417         |
| B13.2 Link                            |                                                                    | 418         |
|                                       | B13.2.1 Outbound and inbound links                                 | 418         |
| B13.3 Flit                            |                                                                    | 419         |
| B13.4 Channel                         |                                                                    | 420         |
|                                       | B13.4.1 Channel dependencies                                       | 420         |
| B13.5 Port                            |                                                                    | 422         |
| B13.6 Node interface defintions       |                                                                    | 423         |
|                                       | B13.6.1 Request Nodes                                              | 423         |
|                                       | B13.6.2 Subordinate Nodes                                          | 424         |
| B13.7 Increasing inter-port bandwidth |                                                                    | 426         |
|                                       | B13.7.1 Multiple interfaces                                        | 426         |
|                                       | B13.7.2 Replicated channels on a single interface                  | 428         |
| B13.8 Channel interface signals       |                                                                    | 430         |
|                                       | B13.8.1 Request, REQ, channel                                      | 430         |
|                                       | B13.8.2 Response, RSP, channel                                     | 430         |
|                                       | B13.8.3 Snoop, SNP, channel                                        | 431         |
|                                       | B13.8.4 Data, DAT, channel                                         | 432         |
| B13.9 Flit packet definitions         |                                                                    | 434         |
|                                       | B13.9.1 Request flit                                               | 434         |
|                                       | B13.9.2 Response flit                                              | 435         |
|                                       | B13.9.3 Snoop flit                                                 | 436         |
|                                       | B13.9.4 Data flit                                                  | 437         |
| B13.10 Protocol flit fields           |                                                                    | 440         |
|                                       | B13.10.1 Quality of Service, QoS                                   | 441         |
|                                       | B13.10.2 Target Identifier, TgtID                                  | 441         |
|                                       | B13.10.3 Source Identifier, SrcID                                  | 441         |
|                                       | B13.10.4 Home Node Identifier, HomeNID                             | 441         |
|                                       | B13.10.5 Return Node Identifier, ReturnNID                         | 441         |
|                                       | B13.10.6 Forward Node Identifier, FwdNID                           | 441         |
|                                       | B13.10.7 Logical Processor Identifier, LPID                        | 442         |
|                                       | B13.10.8 Persistence Group Identifier, PGroupID                    | 442         |
|                                       | B13.10.9 Stash Node Identifier, StashNID                           | 442         |
|                                       | B13.10.10 Stash Node Identifier Valid, StashNIDValid               | 443         |
|                                       | B13.10.11 Stash Logical Processor Identifier, StashLPID            | 443         |
|                                       | B13.10.12 Stash Logical Processor Identifier Valid, StashLPIDValid | 443         |
|                                       | B13.10.13 Stash Group Identifier, StashGroupID                     | 443         |
|                                       | B13.10.14 Transaction Identifier, TxnID                            | 444         |
|                                       | B13.10.15 Return Transaction Identifier, ReturnTxnID               | 444         |
|                                       | B13.10.16 Forwarding Transaction Identifier, FwdTxnID              | 444         |
|                                       | B13.10.17 Data Buffer Identifier, DBID                             | 444         |
|                                       | B13.10.18 Channel opcodes, Opcode                                  | 444         |
|                                       | B13.10.19 Deep persistence, Deep.                                  | 449         |
|                                       | B13.10.20 Address, Addr                                            | 449         |
|                                       | B13.10.21 Non-secure, NS                                           | 450         |
|                                       | B13.10.22 Non-secure extension, NSE                                | 450         |
|                                       | B13.10.23 Size of transaction data, Size                           | 450         |
|                                       | B13.10.24 Memory Attribute, MemAttr                                | 451         |
|                                       | B13.10.25 Snoop Attribute, SnpAttr                                 | 451         |
|                                       | B13.10.26 Do Direct Write Transfer, DoDWT                          | 452         |
|                                       | B13.10.27 Likely Shared, LikelyShared                              | 452         |
|                                       | B13.10.28 Ordering requirements, Order                             | 453         |
|                                       | B13.10.29 Exclusive, Excl                                          | 453         |
|                                       | B13.10.30 CopyAtHome, CAH                                          | 454         |