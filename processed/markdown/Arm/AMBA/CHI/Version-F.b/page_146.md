- Read and Write transactions from the same source to addresses that overlap must remain ordered.
- The No-allocate attribute is an allocation hint and only recommends to the memory system that the transaction is not allocated because of performance reasons. However, the allocation of the transaction is not prohibited.

##### B2.7.4.1.7 Write-Back Allocate

The required behavior for the Write-Back Allocate memory type is the same as for Write-Back No-allocate memory. However, in this case, the allocation hint is a recommendation to the memory system that, for performance reasons, the transaction is allocated.

### B2.7.5 Likely Shared

The LikelyShared attribute is a cache allocation hint. When asserted this attribute indicates that the requested data is likely to be shared by other Request Nodes within the system. This acts as a hint to shared system level caches that the allocation of the cache line is recommended for performance reasons.

There is no required behavior associated with this transaction attribute.

The LikelyShared assertion requirements:

- Can be asserted in:

    - ReadClean
    - ReadNotSharedDirty
    - ReadShared
    - StashOnceUnique, StashOnceSepUnique
    - StashOnceShared, StashOnceSepShared
    - WriteUniquePtl
    - WriteUniqueFull
    - WriteUniqueZero
    - WriteUniquePtlStash
    - WriteUniqueFullStash
    - WriteBackFull
    - WriteCleanFull
    - WriteEvictFull
    - WriteEvictOrEvict

- Must not be asserted in any:

    - Combined Write transactions
    - Dataless or Atomic transactions
    - Other Read or Write transactions

- Is not applicable in:

    - DVMOp or PCrdReturn transaction, and must be set to 0.
    - PrefetchTgt transaction and can take any value.

### B2.7.6 Snoop attribute

The SnpAttr field indicates if a transaction could require snooping.

See Table B13.19 for SnpAttr field encodings.

Table B2.13 shows the snoop attributes for the different transaction types. The following key is used:

- Y Yes, permitted