- Must ensure that a CMO must not be terminated on hitting a Unique copy of a line. The continuation of the CMO is required because the Unique copy could be stale and other dirty copies of the same location exist elsewhere in the cache hierarchy of the system.

#### B2.7.7.1 Reasons for mismatched attributes

Mismatched attributes could happen for various reasons:

- B2.7.7.1.1 Upgrading of Non-shareable Cacheable accesses
- B2.7.7.1.2 Software protocol errors

##### B2.7.7.1.1 Upgrading of Non-shareable Cacheable accesses

Fully coherent Requesters that have Nonshareable\_Cache\_Maint property set to True upgrade all accesses to locations that are marked in page tables as Non-shareable Cacheable to be Shareable Cacheable.

Fully coherent Requesters that have Nonshareable\_Cache\_Maint property set to False will use transactions with SnpAttr = 0 to access these locations. See B16.1.17 Nonshareable\_Cache\_Maint for more details.

With this upgrade:

- A fully coherent Requester uses transactions with SnpAttr = 1 when accessing Non-shareable Cacheable locations.
- All snoops received to locations that were marked Non-shareable Cacheable must behave in the same manner as if the location was originally marked as Shareable Cacheable in the page tables. Additionally, a CMO issued by any Requester in the system subsequently operates on copies that are cached by a fully coherent Requester or interconnect.
- Cache maintenance is enabled on locations marked as Non-shareable in the page tables to be performed by a PE that is different to the one that caused allocation into the cache. This is required to support features such as Realm Management Extensions, see Chapter B10 Realm Management Extension.

Leaving these locations as Non-shareable Cacheable is preferred to high bandwidth IO coherent Requesters, such as GPUs, who do not encounter any snoop filter look-up on all transactions.

When an IO Coherent Requester has been performing stores to the location using Non-snoopable transactions, such as WriteNoSnp, an upgraded version is of that line is possible in an RN-F or interconnect becomes stale.

The interconnect is responsible to ensure stale copies of the cache lines are not made visible to agents that must not observe them and ensure that the most up-to-date copies of the cache lines are not removed from the visibility of agents that must observe them.

##### B2.7.7.1.2 Software protocol errors

Memory accesses from different agents made with mismatched snoopability or cacheability attributes that are not expected can be considered as software protocol errors. A software protocol error can cause loss of coherency and result in corruption of data values. See B9.4.1 Software-based error.

A software protocol error for an access in one 4KB memory region must not cause data corruption in a different 4KB memory region.

For locations held in Normal memory, the use of appropriate software cache maintenance can be used to return memory locations to a defined state.

The use of mismatched memory attributes can result in an RN-F observing a Snoop transaction to the same address where the RN-F would use, or previously have used, Non-snoopable transactions to access. If an RN-F receives a Snoop to a location that is believed to be Non-snoopable, the RN-F must not respond with data and instead send SnpResp\_I. When mismatched attributes are used, there is no defined relationship between the Snoop transaction and the transaction that the RN-F has issued.