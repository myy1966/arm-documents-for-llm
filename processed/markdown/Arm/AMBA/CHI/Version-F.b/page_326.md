## B8.1 Introduction to DVM transactions

DVM transactions are an optional feature used to pass messages that support the maintenance of a virtual memory system.

DVMtransactions support the following operations:

- Non-sync transaction flow, including:

    - TLB Invalidate
    - Branch Predictor Invalidate
    - Physical Instruction Cache Invalidate
    - Virtual Instruction Cache Invalidate

- Sync transaction flow, including:

    - Synchronization

DVM transactions only operate on read-only structures, such as Instruction cache, Branch Predictor, and TLB, and therefore only invalidation operations are required. The concept of cleaning does not apply to a read-only structure. This means that it is functionally correct to invalidate more entries than the DVM message requires, although the extra invalidations can affect performance.

Support for DVM operations on an interface is defined by the DVM\_Support property. See B16.1.19 DVM\_Support for more information.