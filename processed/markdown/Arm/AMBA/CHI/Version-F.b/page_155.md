For Write transactions to Device locations, BE bits must only be asserted for the bytes that are accessed. See B2.8.3 Byte Enables.

### B2.8.3 Byte Enables

Byte Enables (BE) are used alongside Write transactions and Snoop responses with Data.

In the following section, unless explicitly stated otherwise, a reference to a Write transaction includes both the individual Write transaction and the corresponding Combined Write transaction.

In WriteData and Snoop responses, a data BE value of 0 must set the associated data byte value to 0.

In CompData and DataSepResp messages, the BE bits are inapplicable and can take any value.

#### B2.8.3.1 Write transactions

For all Write transactions, BE bits that are not within the data window, specified by Addr and Size, must be deasserted.

An asserted BE in Write transactions indicates that the associated data byte is valid and must be updated in memory or cache. A deasserted BE indicates that the associated data byte is not valid and must not be updated in memory or cache.

A Requester must deassert all BE values in CopyBackWriteData\_I and WriteDataCancel packets.

During data transfers in the following write transactions:

- All BE bits must be asserted, except when write data is a CopyBackWriteData\_I or WriteDataCancel packet:

    - WriteNoSnpFull
    - WriteNoSnpDef
    - WriteBackFull
    - WriteCleanFull
    - WriteEvictFull
    - WriteUniqueFull
    - WriteUniqueFullStash

- Any combination of BE bits is permitted, including asserting all and asserting none:

    - WriteBackPtl
    - WriteUniquePtl
    - WriteUniquePtlStash

For a WriteNoSnpPtl transaction, the following rules apply:

- For a transaction to Normal memory, any combination of BE bits can be asserted during the data transfers. This includes asserting all and asserting none.
- For a transaction to Device memory, BE bits must only be asserted for bytes at or above the address specified in the transaction. Any combination of BE bits can be asserted that meets this requirement. This includes asserting all and asserting none.

#### B2.8.3.2 Atomic transactions

For Atomic transactions, all BE bits within the data window must be asserted.

For Atomic transactions, BE bits that are not within the data window, as specified below by Addr and Size, must be deasserted:

- If Addr is aligned to Size, the Data window is [Addr:(Addr+Size-1)].
- If Addr is not aligned to Size, the Data window is [(Addr-Size/2):(Addr+Size/2-1)].