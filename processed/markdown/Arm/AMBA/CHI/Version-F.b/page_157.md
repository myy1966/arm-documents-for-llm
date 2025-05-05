> **_NOTE:_** For some transactions to Device memory, some data packets can be determined from the address at the start of the transaction to not contain valid data and are redundant. However, it is required that these data packets are transferred.

When a DAT message is split into multiple packets:

- The fields that must be consistent are:

    - TgtID
    - SrcID
    - TxnID
    - HomeNID
    - PBHA
    - Opcode
    - Resp
    - FwdState
    - DataPull
    - DataSource
    - DBID, when the field is applicable
    - CCID
    - TagOp
    - CAH

- The fields that are expected to be consistent, but can vary, are:

    - QoS
    - RespErr
    - DBID, when the field is inapplicable and can take any value
    - TraceTag
    - CBusy

- The fields that are expected to vary are:

    - Data
    - DataID
    - Tag
    - RSVDC
    - BE
    - DataCheck
    - Poison

### B2.8.5 Size, Address, and Data alignment in Atomic transactions

This section describes the data size and alignment requirements for Atomic transactions. It contains the following sections:

- B2.8.5.1 Size
- B2.8.5.2 Address and Data alignment
- B2.8.5.3 Endianness

#### B2.8.5.1 Size

The Size field of the packet specifies the total data size of the Atomic transaction.

For the AtomicCompare transaction, the data size is the sum of the Compare and Swap data values.