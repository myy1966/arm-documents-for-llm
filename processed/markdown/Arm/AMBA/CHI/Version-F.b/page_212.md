## B4.3 Snoop request types

The interconnect generates a Snoop request either in response to a request from a Request Node or due to an internal trigger such as a cache or snoop filter maintenance operation. A Snoop transaction, except for SnpDVMOp, operates on the cached data at the RN-F. A SnpDVMOp transaction carries out a DVM maintenance operation at the target node.

The Home selection of a Snoop to send is based on several criteria:

- Expected or permitted final cache states, required by the request causing the snoop, at the Requester and the snooped nodes.
- Avoid losing any Dirty tags present in the caches being snooped.
- Replacing a Non-forwarding with an equivalent Forwarding snoop, if one exists.
- A Forwarding snoop is permitted to be sent to one RN-F only.
- A stash snoop is permitted to be sent to one RN-F only.
- Snoops are permitted, but not required, to Non-snoopable address locations.

See B4.4 Request transactions and corresponding Snoop requests.

See B4.8 Cache state transitions at a Snoopee for the permitted responses for specific snoop types.

For details of Snoop transaction interaction with the Memory Tagging Extension (MTE) see Chapter B12 Memory Tagging.

**SnpOnceFwd, SnpOnce**

Snoop request to obtain the latest copy of the cache line, preferably without changing the cache line state at the Snoopee.

**SnpStashUnique**

Snoop request recommending that the Snoopee obtains a copy of the cache line in a Unique state:

- It is expected that the snoop for a StashOnceUnique request is not sent if the cache line is cached in Unique state at the Stash target.
- Permitted, but not required, to send the snoop to the Stash target for WriteUniqueFullStash and WriteUniquePtlStash only if the Snoopee does not have a cached copy of the cache line.
- The Snoopee must not return data with the Snoop response.
- Permits the Snoop response to include a Data Pull.
- Data Pull request in the Snoop response is treated as a ReadUnique.
- Must not change the cache line state at the Snoopee.

**SnpStashShared**

Snoop request recommending that the Snoopee obtains a copy of the cache line in a Shared state:

- It is expected to not send the snoop if the cache line is cached at the target.
- The Snoopee must not return data with the Snoop response.
- Permits the Snoop response to include a Data Pull.
- Data Pull request in the Snoop response is treated as a ReadNotSharedDirty.
- Must not change the cache line state at the Snoopee.

**SnpCleanFwd, SnpClean**

Snoop request to obtain a copy of the cache line in Clean state while leaving any cached copy in Shared state. Must not leave the cache line in Unique state.