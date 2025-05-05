- If the cache line is held in a Unique state and the LP exclusive monitor is set, the Exclusive Store has passed and the LP can update the location without issuing a transaction.
- If the cache line is held in a Shared state and the LP exclusive monitor is set, the LP must issue an Exclusive Store transaction. A CleanUnique or MakeReadUnique transaction with the Excl attribute asserted must be used. The LP exclusive monitor must continue to operate and check that the cache line is not updated while the CleanUnique or MakeReadUnique transaction is in progress. An Exclusive CleanUnique transaction response is handled in the following way. The transaction receives a Normal Okay or an Exclusive Okay response. If the transaction receives an Exclusive Okay response, this indicates that the transaction has passed and has completed invalidating all other copies of the cache line. After an exclusive transaction completes with an Exclusive Okay response, the LP must again check the LP exclusive monitor:

    - If the LP exclusive monitor is set, the Exclusive Store has passed and the update is performed.
    - If the LP exclusive monitor is not set, an update to the cache line is indicated to have occurred between the point that the Exclusive Store transaction was issued and the point of completion. The Exclusive Store must fail and the exclusive sequence must be restarted.
    - If the LP has not been able to track the exclusive nature of the cache line, because the cache line has been evicted, the Exclusive Store must fail and the exclusive sequence must be restarted.

If the Exclusive Store transaction receives a Normal Okay response, this indicates another LP has been permitted to progress a transaction associated with an Exclusive Store. The transaction associated with the Exclusive Store, from this LP, has failed and has not propagated to other Logical Processors in the system. When an Exclusive Store transaction completes with a Normal Okay response, the options are:

- The LP can fail the Exclusive Store and restart the exclusive sequence with or without checking the state of the cache line when the access completed.
- The LP can check the LP exclusive monitor, and if the LP exclusive monitor has been reset, the LP must fail the Exclusive Store and restart the exclusive sequence.
- The LP can check the LP exclusive monitor, and if the LP exclusive monitor is set, the LP can repeat the Exclusive Store transaction.

For handling of an Exclusive MakeReadUnique at the Home Node, see B6.3.1.1.2 Home behavior.

### B6.3.4 Exclusive accesses to Non-snoopable locations

The following restrictions apply to Exclusive accesses to Non-snoopable locations:

- The address of an Exclusive access must be aligned to the total number of bytes in the transaction.
- The number of bytes to be transferred in an Exclusive access must be a legal data transfer size. This is 1 byte, 2 bytes, 4 bytes, 8 bytes, 16 bytes, 32 bytes, or 64 bytes.

Failure to observe these restrictions results in behavior that is UNPREDICTABLE.

For Exclusive read and Exclusive write transactions to be considered a pair, the following criteria must apply:

- The addresses of the Exclusive read and the Exclusive write must be identical.
- The value of the control signals, that is MemAttr and SnpAttr of the Exclusive read and the Exclusive write transaction, must be identical.
- The data size in the Exclusive read and the Exclusive write must be identical.
- The LPID value of the Exclusive read must match the LPID value of the Exclusive write transaction.

The minimum number of bytes to be monitored during an exclusive operation is defined by the transaction size. The System monitor can monitor a larger number of bytes, up to 64 bytes, which is the maximum size of an Exclusive access. However, this can result in a successful Exclusive access being indicated as failing because a neighboring byte was updated while the Exclusive access was in progress.