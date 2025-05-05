harmless.

- For a ReadOnceMakeInvalid transaction, it is required that the invalidation of the cache line is committed before the read data response for the transaction. The invalidation of the cache line is not required to have completed at this point, but any later Write transaction from any agent, which starts after this point, is guaranteed not to be invalidated by this transaction.
- Data must be provided to the Requester in either a I, UC, or UD state.
- The Requester must ignore the cache state in the response.

**ReadClean**

Read request to a Snoopable address region to obtain a clean copy of a cache line. This can be used if the Requester is allocating the line to a cache that does not support dirty cache lines, such as an Instruction cache. Data must be provided to the Requester in either UC or SC states only.

**ReadNotSharedDirty**

Read request to a Snoopable address region to carry out a load from the cache line. Data must be provided to the Requester in UC, UD, or SC states only. SD state is not permitted.

> **_NOTE:_** ReadNotSharedDirty is used instead of ReadShared when the Requester cannot accept data in SD state.

**ReadShared**

Read request to a Snoopable address region to carry out a load from the cache line. Data must be provided to the Requester in UC, UD, SC, or SD states.

> **_NOTE:_** ReadShared is used instead of ReadNotSharedDirty when the Requester is able to accept data in the SD state.

**ReadUnique**

Read request to a Snoopable address region to carry out a store to the cache line. Data must be provided to the Requester in UC or UD state only.

**ReadPreferUnique**

Read request to a Snoopable address region requesting a unique copy of a cache line. ReadPreferUnique is used when the Requester prefers, but does not require, the data to be returned in Unique state:

- Data is provided in Unique state unless another Request Node is currently performing an exclusive sequence using the same address. In which case the data is provided in Shared state.
- It is permitted to always provide the data in Shared state to the Requester.

> **_NOTE:_** This request is included in this specification to improve the execution efficiency of an exclusive sequence.

**MakeReadUnique**

Read request to a Snoopable address region requesting a unique copy of a cache line. Typical usage is when the Requester has a shared copy of the cache line and wants to obtain permission to store to the cache line.

> **_NOTE:_** Because data return is guaranteed if the Requester receives an Invalidating snoop and retention of data is required otherwise, resending a request to obtain a Unique copy of the cache line is never required.