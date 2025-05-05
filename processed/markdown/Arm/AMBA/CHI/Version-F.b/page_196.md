**WriteNoSnpDef**

Deferrable write of a full cache line of data from a Request Node to a Non-snoopable address region, or write for a full cache line of data to any address region from the Home to Subordinate. All BE bits must be asserted.

> **_NOTE:_** Multiple Deferrable write transactions are permitted to be outstanding from the same Requester.

**WriteNoSnpZero**

Write data value of 0 without transferring data bytes from a Request Node to a Non-snoopable address region, or write data value of 0 without transferring data bytes to any address region from Home to Subordinate.

**WriteUniqueFull**

Write to a Snoopable address region. Write a full cache line of data to the next-level cache or memory when the cache line is Invalid at the Requester. All BE bits must be asserted.

**WriteUniquePtl**

Write to a Snoopable address region. Write up to a cache line of data to the next-level cache or memory when the cache line is Invalid at the Requester. BE bits must be asserted for the appropriate byte lanes within the specified data size and deasserted in the rest of the data transfer.

**WriteUniqueZero**

Write to a Snoopable address region. Write without data bytes when the data value is 0.

**WriteUniqueFullStash**

Write to a Snoopable address region. Write a full cache line of data to the next-level cache or memory when the cache line is Invalid at the Requester. Also includes a request to the Stash target node to obtain the addressed cache line. All BE bits must be asserted.

**WriteUniquePtlStash**

Write to a Snoopable address region. Write up to a cache line of data to the next-level cache or memory when the cache line is Invalid at the Requester. Also includes a request to the Stash target node to obtain the addressed cache line. BE bits must be asserted for the appropriate byte lanes within the specified data size and deasserted in the remainder of the data transfer.

#### B4.2.3.2 CopyBack transactions

CopyBack transactions are a subclass of Write transactions. CopyBack transactions move coherent data from a cache to the next level cache or memory. Each CopyBack transaction must assert the appropriate BE bits with the data. CopyBack transactions do not require the snooping of other agents in the system.

**WriteBackFull**

WriteBack a full cache line of Dirty data to the next level cache or memory. All BE bits must be asserted except when the write data is CopyBackWriteData\_I.

**WriteBackPtl**

WriteBack up to a cache line of Dirty data to the next level cache or memory. All appropriate BE bits, up to all 64, including none or all, must be asserted.

**WriteCleanFull**

WriteBack a full cache line of Dirty data to the next level cache or memory and retain a Clean copy in the cache. All BE bits must be asserted except when the write data is CopyBackWriteData\_I.

**WriteEvictFull**

WriteBack of UniqueClean data to the next-level cache.

- All BE bits must be asserted except when the write data is CopyBackWriteData\_I.
- The cache line must not propagate beyond its Snoop domain.