    - Not be forwarded directly to the Requester even when instructed by the snoop.

**SC** Shared Clean:

- Other caches could have a shared copy of the cache line.
- The cache line could have been modified with respect to memory.
- The cache is not responsible to write the cache line back to memory on eviction.
- The cache line cannot be modified without invalidating any shared copies and obtaining unique ownership of the cache line.
- In response to a snoop that requests data, the cache line:

    - Is required to not return data if RetToSrc bit is not set.
    - Is expected to return data if RetToSrc bit is set.
    - Is expected to be forwarded directly to the Requester when instructed by the snoop

**SD** Shared Dirty:

- Other caches could have a shared copy of the cache line.
- The cache line has been modified with respect to memory.
- The cache line must be written back to next level cache or memory on eviction.
- The cache line cannot be modified without invalidating any shared copies and obtaining unique ownership of the cache line.
- In response to a snoop that requests data, the cache line:

    - Must be returned to Home when requested.
    - Is expected to be forwarded directly to the Requester when instructed by the snoop.

A cache is permitted to implement a subset of these states.

### B4.1.1 Empty cache line ownership

An empty cache line is a cache line that is held in a Unique state to prevent other copies of the cache line existing. None of the data bytes are valid in an empty cache line. This cache line state is UCE or UDP.

The following are examples of when empty cache line ownership can occur:

- A Requester can deliberately obtain an empty cache line before starting a write, to save system bandwidth. A Requester that expects to write to a cache line can obtain an empty cache line with permission to store, instead of obtaining a valid copy of the cache line.
- A Requester can transition into an empty state if the Requester has a copy of the cache line when permission to store is requested. That copy of the cache line is invalidated before the Requester obtains permission to store. At the completion of the request, this results in the Requester having an empty cache line with permission to store.

### B4.1.2 Ownership of cache line with partial Dirty data

Once ownership of a cache line without data is obtained, the Requester is permitted, but not required, to store to the cache line. If the Requester modifies part of the cache line, the cache line remains partially Unique Dirty. This cache line state is UDP.