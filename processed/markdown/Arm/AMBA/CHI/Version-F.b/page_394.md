## B12.1 Introduction

The Memory Tagging Extension (MTE) is a mechanism that is used to check the correct usage of data held in memory. When a memory location is allocated for a particular use, a memory tag can also be assigned. This memory tag is held alongside that data in memory and is referred to as the Allocation Tag. When the memory location is later accessed, the Requester uses both the address of the location and the tag value that the Requester believes is associated with the location. This tag is referred to as the Physical Address Tag or Physical Tag.

For any access where tag checking is enabled, the Physical Tag is checked against the Allocation Tag. The access always progresses as normal, and the result of the tag check determines whether or not an error condition is signaled.

MTE ensures that a memory access is for its expected purpose, rather than an erroneous or malicious access. MTE can be used at runtime to identify many common programming memory errors, such as buffer-overflow and use-after-free.

The memory tag consists of a 4-bit tag associated with each aligned 16 bytes of data in memory.

The following behavior is supported:

- Memory tagging is permitted only in requests to Normal WriteBack memory.
- Read transactions have an indication in the transaction request that determines whether the Allocation Tag value must be returned alongside the data.
- Checking of the returned Physical Tag against the Allocation Tag is performed by the Requester. In the case where a cache holds the data value, but does not hold the Allocation Tag value, a Read transaction that returns both data and tag must be performed. The data returned is not required to be valid.
- Read requests that require tags to be fetched must not use Forwarding snoops.
- StashOnce transactions that request Allocation Tags. The Allocation Tags are expected to be stashed along with the stashing of data.
- Write transactions that have a Physical Tag supplied alongside the write data that must be checked against the Allocation Tag.
- Checking of the Physical Tag against the Allocation Tag is performed by the Completer. In the case of a mismatch a notification of the failure is required.
- Write transactions that update the Allocation Tag to a new value.
- These Write transactions typically update the data at the same time. However, it is permitted to have no BE bits asserted so that only the tag is updated.
- Write transactions which pass a Dirty or Clean cache line to a downstream cache or memory controller without either updating or checking the tags. These Write transactions always include data and provide an indication whether the Allocation Tag value is also being passed with the data.
- Snoop transactions that return data can also return the associated Allocation Tag. If the tags are Dirty, they must be returned. If the tags are Clean, returning them is optional.
- Cache Maintenance Operations must operate on both the data and the corresponding memory tags.