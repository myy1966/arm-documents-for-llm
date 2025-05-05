Table B4.38 Continued from previous page

| Response received                | Cache line state                     | Action                                                                                                                             |
|----------------------------------|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| RespSepData, DataSepResp\_UC     | Clean copy is given to the Requester | Requester lost the cache line while the transaction was in progress. Separate data and completion responses are given.             |
| RespSepData, DataSepResp\_UD\_PD | Dirty copy is given to the Requester | Requester lost the cache line while the transaction was in progress. Separate data and completion responses are given by the Home. |

Table B4.39 shows the additional permitted responses in the Exclusive MakeReadUnique transaction.

Table B4.39: Additional permitted responses in the MakeReadUnique(Excl) transaction

| Response received            | Global Exclusive check | Shared cached copy      | Copy of the cache line     |
|------------------------------|------------------------|-------------------------|----------------------------|
| Comp\_SC                     | Fail                   | Exists in another cache | Retained by Requester      |
| CompData\_SC                 | Fail                   | Exists in another cache | Could be lost by Requester |
| RespSepData, DataSepResp\_SC | Fail                   | Exists in another cache | Could be lost by Requester |

##### B4.7.1.1.2 Expected snoops

The use of snoops by the Home to invalidate a cache line at the Snoopee in response to a non-Exclusive MakeReadUnique, or an Exclusive MakeReadUnique that passes an Exclusive check, are as follows:

- The Home is expected to use a SnpCleanInvalid snoop:
- The Home is permitted to use SnpUnique instead of SnpCleanInvalid.
- The Home is permitted to use SnpUniqueFwd if the Requester is determined to have lost the cached copy of the cache line.
- If the Home has not invalidated the Requester that sent the MakeReadUnique, it is also permitted to use SnpMakeInalid. The SnpResp\_I response from a SD copy can be used to implicitly transfer the Dirty responsibility.

See B6.3.1.1.2 Home behavior for the types of snoops the Home is expected and permitted to use when an Exclusive MakeReadUnique request fails the Exclusive check.

##### B4.7.1.1.3 Cache line state transitions

The final state of the cache line after a MakeReadUnique transaction depends on the state of the cache line immediately before the transaction response is received. This can be different from the state of the cache line at the point the transaction is issued.

For MakeReadUnique, the Requester must keep a copy of the cache line unless an invalidating snoop is received.

- Invalidating snoops are SnpUnique, SnpUniqueFwd, SnpCleanInvalid, SnpMakeInvalid, SnpUniqueStash, and SnpMakeInvalidStash.