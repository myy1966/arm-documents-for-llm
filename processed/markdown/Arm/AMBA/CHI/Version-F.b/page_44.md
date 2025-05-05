## B2.2 Channel fields

This section gives a brief overview of the channel fields and indicates which fields affect the transaction structure. The associated fields with each channel are described in the following sections:

- B2.2.1 Transaction request fields
- B2.2.2 Response fields
- B2.2.3 Snoop request fields
- B2.2.4 Data fields

The term Transaction Structure is used to describe the different packets that form a transaction. The transaction structure can vary depending on several factors.

### B2.2.1 Transaction request fields

Table B2.2 shows the Request fields associated with a Request packet.

More information on the different transaction structures can be found in B2.3 Transaction structure and B13.9 Flit packet definitions.

Table B2.2: Request channel fields

| Field         | Affects structure   | Description                                                                                                                                                                                              |
|---------------|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QoS           | No                  | Quality of Service priority. Specifies one of 16 possible priority levels for the transaction with ascending values of QoS indicating higher priority levels. See B13.10.1 Quality of Service, QoS.      |
| TgtID         | No                  | Target Identifier. The node identifier of the port on the component to which the packet is targeted. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID and B3.1 System Address Map, SAM. |
| SrcID         | No                  | Source Identifier. The node identifier of the port on the component from which the packet was sent. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.                                   |
| TxnID         | No                  | Transaction Identifier. A transaction has a unique transaction identifier per source node. See B2.4.2 Transaction Identifier, TxnID.                                                                     |
| ReturnNID     | No                  | Return Node Identifier. The recipient node identifier for the Data response, Persist response, or TagMatch response. See B2.4.10 Return Node Identifier, ReturnNID.                                      |
| StashNID      | No                  | Stash Node Identifier. The node identifier of the Stash target. See B2.4.9 Stash Node Identifier, StashNID and B13.10.9 Stash Node Identifier, StashNID.                                                 |
| SLCRepHint    | No                  | System Level Cache Replacement Hint. Forwards cache replacement hints from the Requesters to the caches in the interconnect. See B11.3 SLC Replacement Hint.                                             |
| StashNIDValid | Yes                 | Stash Node Identifier Valid. Indicates that the StashNID field has a valid Stash target value. See B13.10.10 Stash Node Identifier Valid, StashNIDValid.                                                 |
| Endian        | No                  | Endianness. Indicates the endianness of data in the data packet for Atomic transactions. See B2.8.5.3 Endianness.                                                                                        |

Continued on next page