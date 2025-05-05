### B2.2.4 Data fields

Table B2.5 describes the fields associated with a Data packet. Data packets can be sent on the RDAT or WDAT channels. The fields in a Data packet do not affect the transaction structure.

Table B2.5: Data packet fields

| Field      | Description                                                                                                                                                                 |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QoS        | Quality of Service priority. As defined in Table B2.2. See B11.1 Quality of Service (QoS) mechanism.                                                                        |
| TgtID      | Target Identifier. As defined in Table B2.2. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.                                                             |
| SrcID      | Source Identifier. As defined in Table B2.2. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.                                                             |
| TxnID      | Transaction Identifier. As defined in Table B2.2. See B2.4.2 Transaction Identifier, TxnID.                                                                                 |
| HomeNID    | Home Node Identifier. The node identifier of the target of the CompAck response to be sent from the Requester. See B2.4.11 Home Node Identifier, HomeNID.                   |
| PBHA       | Page-based Hardware Attributes. 4 bits from the translation tables that can be used for IMPLEMENTATION DEFINED hardware control. See B11.5 Page-based Hardware Attributes.  |
| Opcode     | Data opcode. Indicates, for example, if the data packet is related to a Read transaction, a Write transaction, or a Snoop transaction. See B13.10.18.4 DAT channel opcodes. |
| RespErr    | Response Error status. Indicates the error status associated with a data transfer. See Chapter B6 Exclusive accesses and B9.1.2 Error response fields.                      |
| Resp       | Response status. Indicates the cache line state associated with a data transfer. See B4.5 Response types.                                                                   |
| DataSource | Data Source. The value indicates the source of the data in a Read Data Data Source indication.                                                                              |
| FwdState   | response. See B11.2 Forward State. Indicates the cache line state associated with a data transfer. See B4.5 Response types.                                                 |
| DataPull   | Data Pull. Indicates the inclusion of an implied Read request in the Data response. See B7.1.1 Snoop requests and Data Pull.                                                |
| CBusy      | Completer Busy. Indicates the current level of activity at the Completer. See B11.6 Completer Busy.                                                                         |
| DBID       | Data Buffer Identifier. The identifier to be used as the TxnID in the response to the Data message. See B2.4.3 Data Buffer Identifier, DBID and B2.6 Ordering.              |
| CCID       | Critical Chunk Identifier. Replicates the address offset of the original Transaction request. See B2.8 Data transfer.                                                       |

Continued on next page