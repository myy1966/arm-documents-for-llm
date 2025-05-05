- Writes can be merged.

Any Read, Dataless, Write, PrefetchTgt, or Atomic transaction type can be used to access a Normal memory location. The transaction type used is determined by the memory operation to be accomplished, and the Snoopable attributes.

#### B2.7.3.3 Cacheable

The Cacheable attribute indicates if a transaction must perform a cache lookup:

- When Cacheable is asserted, the transaction must perform a cache lookup.
- When Cacheable is deasserted, the transaction must access the final destination.

The Cacheable attribute value requirements are:

- Must be asserted for any:

    - Read transaction except ReadNoSnp and ReadNoSnpSep.
    - Dataless transaction except CleanShared, CleanSharedPersist*, CleanInvalid, CleanInvalidPoPA, and MakeInvalid.
    - Write transaction, except WriteNoSnpFull, WriteNoSnpPtl, and WriteNoSnpDef.

- Must not be asserted for any:

    - Device memory transaction
    - WriteNoSnpDef transaction

- Can take any value for:

    - ReadNoSnp or ReadNoSnpSep transaction to a Normal memory location.
    - WriteNoSnpFull and WriteNoSnpPtl transactions to a Normal memory location.
    - CleanShared, CleanSharedPersist*, CleanInvalid, CleanInvalidPoPA, and MakeInvalid.
    - An Atomic transaction.

- Is inapplicable and:

    - Must be set to 0 DVMOp and PCrdReturn.
    - Can take any value in the PrefetchTgt.

> **_NOTE:_** In a transaction that can take any Cacheable value, the value is typically determined from the page table attributes.

#### B2.7.3.4 Allocate

The Allocate attribute is an allocation hint and indicates the recommended allocation policy for a transaction:

- If Allocate is asserted, it is recommended that the transaction is allocated into the cache for performance reasons. However, the cache is permitted to not allocate the transaction.
- If Allocate is deasserted, it is recommended that the transaction is not allocated into the cache for performance reasons. However, the cache is permitted to allocate the transaction.

The Allocate attribute value requirements are:

- Can be asserted for transactions that have the Cacheable attribute asserted, except for ReadOnceMakeInvalid.