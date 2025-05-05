- Combined Write transactions that combine the following Cache Maintenance Operations with Write transactions must be converted to standalone Write transactions:

    - CleanShared
    - CleanInvalid
    - MakeInvalid

### B16.2.3 BROADCASTPERSIST

The BROADCASTPERSIST signal is used to control the issuing of CleanSharedPersist and CleanSharedPersistSep Cache Maintenance Operations.

When the BROADCASTPERSIST signal is present and deasserted, CleanSharedPersist and CleanSharedPersistSep transactions are converted to CleanShared.The conversion applies to both standalone CMO and Combined Write transactions.

> **_NOTE:_** The issuing of the CleanShared is controlled by the **BROADCASTINNER**, **BROADCASTOUTER**, and **BROADCASTCACHEMAINT** signals.

### B16.2.4 BROADCASTATOMIC

The BROADCASTATOMIC signal is used to control the generation of Atomic transactions:

- When asserted, the interface is permitted, but not required, to generate Atomic transactions.
- When deasserted, the interface must not generate Atomic transactions.

A Request Node is not required to make use of Atomic transactions. A Request Node that does not make use of Atomic transactions itself, needs no added functionality to be compatible with an interconnect that supports Atomic transactions.

A Request Node that supports atomic operations but does not include support for the execution of atomic operations must be able to send Atomic transactions.

See B16.3 Atomic transaction support.

### B16.2.5 BROADCASTICINVAL

The BROADCASTICINVAL signal at each Request Node is used to inform the Request Node that broadcasting of Instruction Cache (ICache) invalidations using the DVM mechanism is required:

- When asserted, DVMOp for ICache Invalidations must be sent to the interconnect.
- When deasserted, DVMOp for ICache invalidations are not required to be sent to the interconnect.

In a system where all Instruction Caches are fully coherent the hardware coherency mechanism automatically invalidates all ICache copies on a cache line update, In such systems, it is not necessary to broadcast ICache invalidation operations.

If a system contains one or more Instruction Caches that are not updated by the hardware coherency mechanism, it is necessary for ICache invalidation operations to be broadcast using DVM transactions.

### B16.2.6 BROADCASTMTE

The BROADCASTMTE signal is used to control the issuing of requests with MTE beyond the interface: