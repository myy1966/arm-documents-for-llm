#### B4.2.6.1 DVM transactions

DVMtransactions are used for virtual memory system maintenance.

**DVMOp**

DVMOperation. Actions include the passing of messages between components within a distributed virtual memory system. See Chapter 8 DVM Operations for details.

#### B4.2.6.2 Prefetch transaction

The Prefetch target transaction is used to speculatively fetch data from main memory.

**PrefetchTgt**

Prefetch Target. A Request to a Snoopable memory address, sent from a Request Node directly to a Subordinate Node:

- The PrefetchTgt transaction does not include a response.
- The request can be used by the Subordinate Node to fetch the data from off-chip memory. The data can subsequently be buffered in anticipation of a subsequent Read request to the same location.
- The request does not include a response nor RetryAck. The Requester can deallocate the request as soon as the request is sent.
- The Receiver must accept the request without dependency on receiving of a subsequent Read request to the same address.
- The Receiver is permitted to initiate an internal action or discard the request without any further action.
- Data read from off-chip memory using PrefetchTgt must not hold Subordinate Node resources waiting indefinitely for a future Read request to the same address.
- The following fields are inapplicable and can take any value:

    - TxnID
    - Order
    - Endian
    - Size
    - MemAttr
    - SnpAttr
    - Excl
    - LikelyShared