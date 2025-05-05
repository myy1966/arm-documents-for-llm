## B2.4 Transaction identifier fields

Each transaction consists of a number of different packets that are transferred across the interconnect. A set of identifier fields, within a packet, are used to provide additional information about a packet.

The field that routes packets across the interconnect:

- B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID

The fields that relate all the packets associated with a single transaction are:

- B2.4.2 Transaction Identifier, TxnID
- B2.4.3 Data Buffer Identifier, DBID
- B2.4.4 Return Transaction Identifier, ReturnTxnID
- B2.4.5 Forward Transaction Identifier, FwdTxnID

The field that identifies the individual data packets within a transaction:

- B2.4.6 Data Identifier, DataID, and Critical Chunk Identifier, CCID

The fields that identify individual processing agents within a single Requester:

- B2.4.7 Logical Processor Identifier, LPID
- B2.4.8 Stash Logical Processor Identifier, StashLPID

The field that identifies the target node for a Stash transaction:

- B2.4.9 Stash Node Identifier, StashNID

The field that identifies the recipient node for the Data response, Persist response, or TagMatch response:

- B2.4.10 Return Node Identifier, ReturnNID

The field that identifies the recipient node for the Data response:

- B2.4.12 Forward Node Identifier, FwdNID

The field that is used to identify the recipient node for the CompAck response:

- B2.4.11 Home Node Identifier, HomeNID

The field that is used to identify different sets of transactions:

- B2.4.13 Persistence Group Identifier, PGroupID
- B2.4.14 Stash Group Identifier, StashGroupID
- B2.4.15 Tag Group Identifier, TagGroupID

### B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID

A transaction request includes a TgtID that identifies the target node, and a SrcID that identifies the source node. These identifiers are used to route packets across the interconnect.

### B2.4.2 Transaction Identifier, TxnID

A transaction request includes a TxnID that is used to identify the transaction from a given Requester. It is required that the TxnID, except for PrefetchTgt, must be unique for a given Requester. The Requester is identified by the SrcID. This ensures that any returning read data or response information can be associated with the correct transaction.

A 12-bit field is defined for the TxnID with the number of outstanding transactions limited to 1024. A Requester is permitted to reuse a TxnID value after receiving either: