- CleanUnique, MakeUnique
- Evict
- Independent Stash transactions

    - StashOnceUnique, StashOnceSepUnique, StashOnceShared, StashOnceSepShared

- Cache Maintenance transactions

    - CleanShared, CleanSharedPersist, CleanSharedPersistSep, CleanInvalid, CleanInvalidPoPA, MakeInvalid

Dataless transactions have the following common characteristics:

- Data must not be included in the completion response.
- The Request can result in data movement among other agents in the system.
- The Request can result in a cache state change at the Requester. See Table B4.10 for expected and permitted initial cache and Table B4.11 for final cache state at the Requester for each of the Dataless transactions.
- The Request can result in a cache state change at the other Request Nodes in the system. See Table B4.12 for expected and permitted cache states at the peer Request Nodes for each of the Dataless transactions.

See Chapter B6 Exclusive accesses for details on Exclusive attribute in Dataless transactions.

**CleanUnique**

Request to a Snoopable address region to change the cache state at the Requester to Unique to carry out a store to the cache line. Typical usage is when the Requester has a shared copy of the cache line and wants to obtain permission to store to the cache line. Any dirty copy of the cache line at a snooped cache must be written back to the memory.

**MakeUnique**

Request to a Snoopable address region to obtain ownership of the cache line without a data response. MakeUnique is only used when the Requester guarantees to carry out a store to all bytes of the cache line. Any dirty copy of the cache line at a snooped cache must be invalidated without carrying out a data transfer.

**Evict**

Used to indicate that a Clean cache line is no longer cached by the Request Node.

**StashOnceUnique, StashOnceSepUnique**

Request to a Snoopable address region to attempt to move the addressed cache line to a targeted cache to enable the target to store that line. The request includes:

- A valid node ID of another Request Node as the Stash target, along with an optional LPID within that node. When a valid target is not specified, the addressed cache line can be fetched to be cached at the request Completer.
- It is recommended, but not required, that the other agent is snooped to indicate obtaining the addressed cache line and ensures that being in a cache state suitable for writing to the cache line.
- The DataPull request from the target Request Node is treated as a ReadUnique Request.

See Chapter 7 Cache Stashing.

**StashOnceShared, StashOnceSepShared**

Request to a Snoopable address region to attempt to move the addressed cache line to a targeted cache. The request includes:

- The node ID of another Request Node. Optionally, the request can include the LPID within that node. When a valid target is not specified, the addressed cache line can be fetched to be cached at the request Completer.
- It is recommended, but not required, that the other agent is snooped to indicate that the other agent obtains the addressed cache line.