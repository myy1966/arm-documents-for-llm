- It is recommended that progress on Exclusive requests from one PAS is independent of progress on Exclusive requests from any other PAS.

### B6.3.3 Exclusive accesses to Snoopable locations

This section describes the behavior of an LP when performing Exclusive accesses to a Snoopable address location.

#### B6.3.3.1 Snoopable Exclusive Load

The LP starts an exclusive sequence with an Exclusive Load. The start of the exclusive sequence must set the LP exclusive monitor.

An LP wanting to perform an Exclusive access to a Snoopable location could already hold the cache line in its local cache:

- If the LP holds the cache line in a Unique state, it is permitted, but not recommended, that an Exclusive Load transaction is performed.
- If the LP holds the cache line in a Shared state, it is permitted, but not required, that an Exclusive Load transaction is performed.
- If the LP does not hold a copy of the cache line, it is recommended that the LP uses an Exclusive Load transaction to obtain the cache line. It is permitted to use ReadClean, ReadShared, ReadNotSharedDirty, or ReadPreferUnique without the Excl attribute asserted.

#### B6.3.3.2 Snoopable Exclusive Load to Snoopable Exclusive Store

Typically, after the execution of an Exclusive Load, an LP calculates a new value to store to the location before attempting the Exclusive Store.

It is not required that an LP always completes an Exclusive sequence. For example, the value obtained by the Exclusive Load can indicate that a semaphore is held by another LP and that the value cannot be changed until the semaphore is released by the other LP. Therefore, a new Exclusive sequence can be started with no attempt to complete the current Exclusive sequence.

During the time between the Exclusive Load and the Exclusive Store, the LP exclusive monitor must monitor the location to determine whether another LP could have updated the location.

#### B6.3.3.3 Snoopable Exclusive Store

An LP must not permit an Exclusive Store transaction to be in progress at the same time as any transaction that registers that it is performing an exclusive sequence. The LP must wait for all messages for any such transaction to be exchanged, or to receive a RetryAck response, before issuing an Exclusive Store transaction. The transactions that register that an LP is performing an exclusive sequence are:

- Exclusive Load transactions to any location.
- Exclusive Store transactions to any location.

When an LP executes an Exclusive Store the following behavior is required:

- If the LP exclusive monitor has been reset the Exclusive Store must fail and the LP must not issue an Exclusive Store transaction. The LP must restart the exclusive sequence.

> **_NOTE:_** When the LP monitor has been reset, not issuing a transaction for an Exclusive Store that must eventually fail avoids unnecessary invalidation of other copies of the cache line.