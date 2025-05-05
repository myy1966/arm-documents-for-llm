## B4.1 Cache line states

The action required when a protocol node accesses a cache line is determined by the cache line state. The protocol defines the following cache line states:

**I** Invalid:

- The cache line is not present in the cache.

**UC** Unique Clean:

- The cache line is present only in this cache.
- The cache line has not been modified with respect to memory.
- The cache line can be modified without notifying other caches.
- In response to a snoop that requests data, the cache line is permitted, but not required, to be:

    - Returned to Home when requested.
    - Forwarded directly to the Requester when instructed by the snoop.

**UCE** Unique Clean Empty:

- The cache line is present only in this cache.
- The cache line is in a unique state but none of the data bytes are valid.
- The cache line can be modified without notifying other caches.
- In response to a snoop that requests data, the cache line must not be:

    - Returned to Home even when requested.
    - Forwarded directly to the Requester even when instructed by the snoop.

**UD** Unique Dirty:

- The cache line is present only in this cache.
- The cache line has been modified with respect to memory.
- The cache line must be written back to next level cache or memory on eviction.
- The cache line can be modified without notifying other caches.
- In response to a snoop that requests data, the cache line:

    - Must be returned to Home when requested.
    - Is expected to be forwarded directly to the Requester when instructed by the snoop.

**UDP** Unique Dirty Partial:

- The cache line is present only in this cache.
-  The cache line is unique. The cache line could have some bytes valid, where some includes none or all bytes.
- The cache line has been modified with respect to memory.
-  When the cache line is evicted, data from next level cache or memory must be merged with the evicted cache line to form the complete valid cache line.
- The cache line can be modified without notifying other caches.
- In response to a snoop that requests data, the cache line must:

    - Be returned to Home.