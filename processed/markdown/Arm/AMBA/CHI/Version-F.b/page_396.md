## B12.3 Tag coherency

This section summarizes the tag coherency features.

Allocation Tags that are cached are kept hardware coherent. The coherence mechanism is the same as data coherence.

Applicable tag cached states are: Invalid, Clean, and Dirty. A cache line that is either Clean or Dirty is Valid.

Constraints on the combination of data cache state and tag cache state are:

- Tags can be Valid only when data is Valid.
- Tags can be Invalid when data is Valid.
- Both data and tags are Unique when a cache line is in a Unique state.
- Both data and tags are Shared when a cache line is in a Shared state.
- When a cache line with Dirty tags is evicted:

    - Both data and tags must be treated as Dirty.
    - The tags must be either written back to memory or passed Dirty [\_PD] by Home to another cache.

- When Clean tags are evicted from a cache, they can be sent to other caches or dropped silently.
- When Clean tags are evicted with Dirty data, Clean tags can be transferred downstream of PoC along with Dirty data.