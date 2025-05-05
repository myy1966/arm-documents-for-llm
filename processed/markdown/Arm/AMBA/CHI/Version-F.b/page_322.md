## B7.4 Stash target identifiers

For all Stash requests, both options of specified and non-specified Stash target are supported.

### B7.4.1 Stash target specified

If the Stash target is available in the Stash request, Home sends the snoop with a stash hint to the specified target. The specified target can be a Request Node or an LP within a Request Node.

### B7.4.2 Stash target not specified

The Home Node that receives a WriteUniquePtlStash or WriteUniqueFullStash request without a Stash target does the following:

- If the cache line is cached in a Unique state at a Request Node, the Home can treat that Request Node as the Stash target.
- If the cache line is not cached in a Unique state, the Home must only send SnpUnique as required, and must not send SnpUniqueStash to any Request Node.
- For WriteUniquePtlStash, if the cache line is not in any cache, it is recommended that he Home prefetches and allocates the cache line in the system cache. It is permitted, but not recommended, to perform a partial write to main memory.
- For WriteUniqueFullStash, if the cache line is not in any cache, Home is permitted to allocate the cache line in the shared system cache.

The Home Node that receives a StashOnce or StashOnceSep request without a Stash target does the following:

- If the cache line is not cached in any peer cache, it is recommended that the cache line is allocated in the shared system cache.
- If the cache line is cached in a peer cache, it is IMPLEMENTATION DEFINED if a snoop is sent to transfer a copy of the cache line and allocate the cache line in the shared system cache. For StashOnceUnique and StashOnceSepUnique, it is IMPLEMENTATION DEFINED if all cached copies are invalidated before allocating the cache line in the shared system cache.