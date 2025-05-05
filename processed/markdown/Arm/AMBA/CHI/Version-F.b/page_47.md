Table B2.3: Response packet fields

| Field        | Description                                                                                                          |
|--------------|----------------------------------------------------------------------------------------------------------------------|
| QoS          | Quality of Service priority. As defined in Table B2.2. See B11.1 Quality of Service (QoS) mechanism.                 |
| TgtID        | Target Identifier. As defined in Table B2.2. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.      |
| SrcID        | Source Identifier. As defined in Table B2.2. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.      |
| TxnID        | Transaction Identifier. As defined in Table B2.2. See B2.4.2 Transaction Identifier, TxnID.                          |
| Opcode       | Response opcode. Specifies response type. See B13.10.18.2 RSP channel opcodes.                                       |
| RespErr      | Response Error status. As defined in Table B2.5. See Chapter B6 Exclusive accesses and B9.1.2 Error response fields. |
| Resp         | Response status. As defined in Table B2.5. See B4.5 Response types.                                                  |
| FwdState     | Forward State. As defined in Table B2.5. See B13.10.49 Forward State, FwdState.                                      |
| DataPull     | Data Pull. As defined in Table B2.5. See B7.1.1 Snoop requests and Data Pull.                                        |
| CBusy        | Completer Busy. As defined in Table B2.5. See B11.6 Completer Busy.                                                  |
| DBID         | Data Buffer Identifier. As defined in Table B2.5. See B2.4.3 Data Buffer Identifier, DBID and B2.6 Ordering.         |
| PGroupID     | Persistence Group Identifier. As defined in Table B2.2. See B13.10.8 Persistence Group Identifier, PGroupID.         |
| StashGroupID | Stash Group Identifier. As defined in Table B2.2. See B13.10.13 Stash Group Identifier, StashGroupID.                |
| TagGroupID   | Tag Group Identifier. As defined in Table B2.2. See B13.10.43 Tag Group Identifier, TagGroupID.                      |
| PCrdType     | Protocol Credit Type. See B2.9.2.2 PCRdType.                                                                         |
| TagOp        | Tag Operation. As defined in Table B2.2. See B13.10.40 Tag Operation, TagOp.                                         |
| TraceTag     | Trace Tag. As defined in Table B2.2. See Chapter B11 System Control, Debug, Trace, and Monitoring.                   |

### B2.2.3 Snoop request fields

Table B2.4 shows the Snoop request fields. Many of the Snoop request fields are the same as fields defined for the Request channel.