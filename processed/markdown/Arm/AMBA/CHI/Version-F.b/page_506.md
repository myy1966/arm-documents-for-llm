## B16.3 Atomic transaction support

The CHI component support requirements for Atomic transactions are described in the following sections:

- B16.3.1 Request Node support
- B16.3.2 Interconnect support
- B16.3.3 Subordinate Node support

### B16.3.1 Request Node support

A Requester component is required to support a mechanism to suppress the generation of Atomic transactions to ensure compatibility in systems where Atomic transactions are not supported. A Requester can use the optional interface pin **BROADCASTATOMIC** to determine whether Atomic transactions are transmitted.

A Request Node is not required to make use of Atomic transactions. A Request Node that does not use Atomic transactions itself needs no added functionality to be compatible with an interconnect that supports Atomic transactions.

A Request Node that supports atomic operations but does not include support for the execution of atomic operations must be able to send Atomic transactions.

For a Request Node that supports both the execution of atomic operations as well as the sending of Atomic transactions the following applies:

For cacheable locations, both Snoopable and Non-snoopable, a Request Node is able to perform an atomic operation locally without generating an Atomic transaction at its interface. To achieve this, the Requester obtains a copy of the location in its local cache, in the same manner that the Requester would for a store operation, and subsequently performs the atomic operation within its local cache. For cacheable locations that are Snoopable, if the contents of the cache line are updated and the cache line was not previously Dirty, the cache line must be marked as Dirty.

### B16.3.2 Interconnect support

Interconnect support for Atomic transactions is optional.

The Atomic\_Transactions property is used to indicate that an interconnect supports Atomic transactions.

If Atomic transactions are not supported by the interconnect, all attached Request Nodes must be configured to not generate Atomic transactions. The BROADCASTATOMIC pin can be used for this purpose, when implemented. See B16.3.1 Request Node support.

For interconnects that support Atomic transactions, atomic operation execution can be supported at any point within an interconnect, including passing an Atomic transaction downstream to a Subordinate Node.

Atomic transactions are not required to be supported for every address location.

If Atomic transactions are supported for a given Snoopable address location, they must be supported for the complete Snoopable address range.

If Atomic transactions are not supported for a given address location, an appropriate Error response can be given for the Atomic transaction. See B9.1.4.4 Atomic transactions.

For transactions to a Device, the Atomic transaction must be passed to the appropriate endpoint Subordinate. If the Subordinate is configured to not support Atomic transactions, the interconnect must return an Error response for the transaction.

For Non-snoopable transactions, the Atomic transaction must be performed either:

- At a point, or past a point, where the transaction is visible to all other agents.