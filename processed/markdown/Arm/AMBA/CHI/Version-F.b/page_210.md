Table B4.24 – Continued from previous page

| Request       | Size (bytes) | SnoopMe | DoDWT | MemAttr A C D E                       | Order    | LikelyShared | ExpCompAck |
|---------------|--------------|---------|-------|---------------------------------------|----------|--------------|------------|
| AtomicCompare | 2,4,8,16,32  | 0 ᵃ     | 0     | 0010                                  | 11       | 0 ᵃ          | 0 ᵃ        |
| AtomicCompare | 2,4,8,16,32  | 0 ᵃ     | 0     | 0011                                  | 00,10,11 | 0 ᵃ          | 0 ᵃ        |
| AtomicCompare | 2,4,8,16,32  | 0 ᵃ     | 0     | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0 ᵃ          | 0 ᵃ        |

- ᵃ The field is inapplicable and must be set to 0.

##### B4.2.5.2.1 Communicating node pair

See Chapter C2 Communicating Nodes for expected and permitted node pairs for each Atomic transaction.

#### B4.2.5.3 Initial cache state at the Requester

The Requester cache state permitted at the issue of the Atomic transaction is any state.

At the time of issuing an Atomic transaction, if the Requester determines the cache state is not Invalid, or cannot determine that the cache state is Invalid, the value of SnoopMe in the Atomic request must be set to 1.

#### B4.2.5.4 Final cache state at the Requester

The Requester cache state permitted at the completion of an Atomic transaction is Invalid.

#### B4.2.5.5 Peer cache state

The peer Request Node cache state at the completion of Atomic transactions is Invalid.

### B4.2.6 Other transactions

This section describes the protocol transactions that carry out miscellaneous actions.

See Chapter B12 Memory Tagging for a description of the Memory Tagging mechanism.

For information on the permitted MTE TagOp values for each miscellaneous request see Table B12.3.

See Chapter C2 Communicating Nodes for expected and permitted node pairs for other transactions.