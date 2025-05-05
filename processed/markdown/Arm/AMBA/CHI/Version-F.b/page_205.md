**AtomicStore**

- Sends a single data value with an address and the atomic operation to be performed.
- The target, a Home Node or a Subordinate Node, performs the required operation on the address location specified with the data supplied in the Atomic transaction.
- The target returns a completion response without data.
- Unlike in AtomicLoad transactions, the original value of AtomicStore transactions at the addressed location is not returned to the Requester.
- Number of operations supported is 8.

Table B4.20 shows the eight operations supported by the AtomicStore transaction.

Each of the AtomicStore operations apply to 1 byte, 2 byte, 4 byte, or 8 byte data sizes.

Table B4.20: AtomicStore operations

| Operation | Action                                                                                       |
|-----------|----------------------------------------------------------------------------------------------|
| STADD     | Update location with: (TxnData + InitialData)                                                |
| STCLR     | Update location with bitwise: (InitialData AND (NOT TxnData))                                |
| STEOR     | Update location with bitwise: (InitialData XOR TxnData)                                      |
| STSET     | Update location with bitwise: (InitialData OR TxnData)                                       |
| STSMAX    | Update location with TxnData if: (((Signed INT) TxnData - (Signed INT) InitialData) > 0)     |
| STSMIN    | Update location with TxnData if: (((Signed INT) TxnData - (Signed INT) InitialData) < 0)     |
| STUMAX    | Update location with TxnData if: (((Unsigned INT) TxnData - (Unsigned INT) InitialData) > 0) |
| STUMIN    | Update location with TxnData if: (((Unsigned INT) TxnData - (Unsigned INT) InitialData) < 0) |

**AtomicLoad**

- Sends a single data value with an address and the atomic operation to be performed.
- The target, a Home Node or a Subordinate Node, performs the required operation on the address location specified with the data value supplied in the Atomic transaction.
- The target returns the completion response with data. The data value is the original value at the addressed location.
- Number of operations supported is eight.