Table B2.4: Snoop request fields

| Field          | Affects structure   | Description                                                                                                                                                                |
|----------------|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QoS            | No                  | Quality of Service priority. As defined in Table B2.2. See B11.1 Quality of Service (QoS) mechanism.                                                                       |
| SrcID          | No                  | Source Identifier. As defined in Table B2.2. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.                                                            |
| TxnID          | No                  | Transaction Identifier. As defined in Table B2.2. See B2.4.2 Transaction Identifier, TxnID.                                                                                |
| FwdNID         | No                  | Forward Node Identifier. The node identifier of the original Requester. See B2.4.12 Forward Node Identifier, FwdNID.                                                       |
| PBHA           | No                  | Page-based Hardware Attributes. 4 bits from the translation tables that can be used for IMPLEMENTATION DEFINED hardware control. See B11.5 Page-based Hardware Attributes. |
| FwdTxnID       | No                  | Forward Transaction Identifier. The transaction identifier used in the Request by the original Requester. See B2.4.5 Forward Transaction Identifier, FwdTxnID.             |
| StashLPIDValid | No                  | Stash Logical Processor Identifier Valid. As defined in Table B2.2. See B7.5 Stash messages.                                                                               |
| StashLPID      | No                  | Stash Logical Processor Identifier. As defined in Table B2.2. See B7.5 Stash messages.                                                                                     |
| VMIDExt        | No                  | Virtual Machine Identifier Extension. See B8.3.3 Snoop DVMOp field value restrictions.                                                                                     |
| Opcode         | Yes                 | Snoop opcode. See B13.10.18.3 SNP channel opcodes.                                                                                                                         |
| Addr           | No                  | Address. The address of the memory location being accessed for Snoop requests. See B2.7.1 Address and B13.10.20 Address, Addr.                                             |
| NS             | No                  | Non-secure. As defined in Table B2.2. See B2.7.2 Physical Address Space, PAS.                                                                                              |
| NSE            | No                  | Non-secure Extension. As defined in Table B2.2. See B2.7.2 Physical Address Space, PAS.                                                                                    |
| DoNotGoToSD    | No                  | Do Not Go To SD state. Controls Snoopee use of SD state. See B4.10 Do not transition to SD.                                                                                |
| RetToSrc       | Yes                 | Return to Source. Instructs the Receiver of the snoop to return data with the Snoop response. See B4.9 Returning Data with Snoop response.                                 |
| TraceTag       | No                  | Trace Tag. As defined in Table B2.2. See Chapter B11 System Control, Debug, Trace, and Monitoring.                                                                         |
| MPAM           | No                  | Memory System Resource Partitioning and Monitoring. As defined in Table B2.2. See B11.4 MPAM.                                                                              |

> **_NOTE:_** This specification does not define a TgtID field for the Snoop request. See B3.3 TgtID determination.