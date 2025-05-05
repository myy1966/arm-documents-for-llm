## B6.2 Exclusive monitors

The progress of an exclusive sequence is tracked by an exclusive monitor. The location of the monitor and the request type generated to support the Exclusive accesses depends on the memory attributes of the address.

The attributes of Exclusive accesses must be such that they are guaranteed to be observed by an exclusive monitor. For example, if there is a cache between the Requester and monitor, the Exclusive accesses should be Non-cacheable.

### B6.2.1 Snoopable memory location

For a Snoopable memory location two monitors are defined:

**LP monitor**

Each LP within an RN-F must implement an exclusive monitor that observes the location used by an exclusive sequence. The LP monitor is set when the LP executes an Exclusive Load. The LP monitor is reset when either:

- The location is updated by another LP, indicated by an Invalidating snoop request to the same address.
- There is a store to the location by the same LP. If the store from the same LP is Non-exclusive, resetting the monitor is IMPLEMENTATION DEFINED.

**PoC monitor**

An HN-F must implement a PoC monitor that can pass or fail an Exclusive Store transaction. A pass indicates that the transaction has been propagated to other coherent RN-Fs. A fail indicates that the transaction has not been propagated to other coherent RN-Fs and therefore the Exclusive Store cannot pass. The monitor is used to ensure an Exclusive Store transaction from an LP is only successful if the LP could not have received a snoop transaction relating to an Exclusive Store to the same address from another LP, after its own Exclusive Store transaction is issued. The minimum requirement of the PoC monitor is to record when any LP performs a Snoopable transaction related to an exclusive sequence. If an LP has performed a transaction related to an exclusive sequence, and subsequently performs an Exclusive Store transaction before a successful Exclusive Store transaction from another LP is scheduled, the Exclusive Store transaction must be successful. The monitor must support the parallel monitoring of all exclusive-capable Logical Processors in the system. When the HN-F receives a transaction associated with an Exclusive Load or an Exclusive Store, the monitor registers that the LP is attempting an exclusive sequence. When the HN-F receives an Exclusive Store transaction:

- If the PoC monitor has registered that the LP is performing an exclusive sequence, that is, the LP has not been reset by an Exclusive Store transaction from another LP, the Exclusive Store transaction is successful and is permitted to proceed. In such a case, registered attempts of all other LPs must be reset. It is recommended, but not required, that the PoC monitor for the successful LP is left as registered.
- If the PoC monitor has not registered that the LP is performing an exclusive sequence, that is, the LP has been reset by an Exclusive Store from another LP, the Exclusive Store transaction is failed and is not permitted to proceed. The monitor must register that the LP is attempting an Exclusive sequence.

> **_NOTE:_** A successful Exclusive Store transaction from an LP does not have to reset that the LP is performing an exclusive sequence. The LP can continue to perform a sequence of Exclusive Store transactions, which are all successful, until another LP performs a successful Exclusive Store transaction. For store transactions in which the LP is not identifiable, the store must be handled as from a different LP than the one which set the monitor.