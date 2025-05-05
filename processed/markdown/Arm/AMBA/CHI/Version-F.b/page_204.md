The MemAttr and SnpAttr field values in a Combined Write request correspond to the memory attributes of the Write request. When the write and the CMO transactions are separated, the Write transaction inherits the MemAttr and SnpAttr values of the original combined request. The SnpAttr and Cacheable bit values of the separated CMO transaction must be set to the most pervasive.

### B4.2.5 Atomic transactions

An Atomic transaction permits a Requester to issue a transaction with a memory address and an operation to be performed on the memory address to the interconnect. This transaction type moves the operation closer to where the data resides and is useful for atomically executing an operation and updating the memory location in a performance efficient manner.

Without an Atomic transaction, an atomic operation has to be executed using a sequence of memory accesses. These accesses could rely on Exclusive reads and writes.

By using an Atomic transaction:

- A more deterministic latency can be estimated for atomic operations.
- The blocking period of access to the memory location being modified is reduced, which subsequently reduces the impact on the forward progress of memory accesses by other agents.
- Providing fairness among different Requesters accessing a memory location becomes simpler, because accessing of that memory location by an atomic operation is arbitrated at the Point of Serialization (PoS) or Point of Coherence (PoC).

This specification defines the following terms relating to atomic operations and Atomic transactions:

**Atomic operation**

The execution of a function involving multiple data values such that, the loading of the original value, the execution of the function, and the storing of the updated value, occurs in an atomic manner. This means that no other agent has access to the location during the entire operation.

**Atomic transaction**

A transaction that is used to pass an atomic operation, along with the data values required for the execution of the atomic operation, from one agent in a system to another, so that the atomic operation can be carried out by a different component in the system than the component that requires the operation to be performed.

#### B4.2.5.1 Atomic transaction types

The CHI protocol defines four Atomic transaction types:

- AtomicStore
- AtomicLoad
- AtomicSwap
- AtomicCompare

See Chapter B12 Memory Tagging for a description of the Memory Tagging mechanism.

For information on the permitted MTE TagOp values for each Atomic request, see Table B12.3.

The following terminology is used to refer to the different data elements in the execution of an atomic operation:

**TxnData** The write data in the AtomicLoad, and AtomicStore transactions.

**CompareData** The compare value in the AtomicCompare transaction.

**SwapData** The swap value in the AtomicCompare, and AtomicSwap transactions.

**InitialData** The content of the addressed location before the atomic operation.

Enumeration of the four Atomic transaction types is as follows: