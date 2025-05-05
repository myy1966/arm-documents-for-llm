Table B4.21 shows the 8 operations supported by the AtomicLoad transaction.

Each of the AtomicLoad operations applies to 1 byte, 2 byte, 4 byte, or 8 byte data sizes.

Table B4.21: AtomicStore operations

| Operation | Action                                                                                       |
|-----------|----------------------------------------------------------------------------------------------|
| LDADD     | Update location with: (TxnData + InitialData)                                                |
| LDCLR     | Update location with bitwise: (InitialData AND (NOT TxnData))                                |
| LDEOR     | Update location with bitwise: (InitialData XOR TxnData)                                      |
| LDSET     | Update location with bitwise: (InitialData OR TxnData)                                       |
| LDSMAX    | Update location with TxnData if: (((Signed INT) TxnData - (Signed INT) InitialData) > 0)     |
| LDSMIN    | Update location with TxnData if: (((Signed INT) TxnData - (Signed INT) InitialData) < 0)     |
| LDUMAX    | Update location with TxnData if: (((Unsigned INT) TxnData - (Unsigned INT) InitialData) > 0) |
| LDUMIN    | Update location with TxnData if: (((Unsigned INT) TxnData - (Unsigned INT) InitialData) < 0) |

**AtomicSwap**

- Sends a single data value, the swap value, together with the address of the location to be operated on.
- The target, a Home Node or a Subordinate Node, swaps the value at the address location with the data value supplied in the transaction.
- The target returns the completion response with data. The data value is the original value at the addressed location.
- Number of operations supported is 1.

**AtomicCompare**

- Sends two data values, the compare value and the swap value, with the address of the location to be operated on.
- The target, a Home Node or a Subordinate Node, compares the value at the addressed location with the compare value:

    - If the values match, the target writes the swap value to the addressed location.
    - If the values do not match, the target does not write the swap value to the addressed location.