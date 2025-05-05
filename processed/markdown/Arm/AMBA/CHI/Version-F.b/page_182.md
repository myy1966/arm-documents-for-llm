**ReadNoSnp**

Read request by a Request Node to a Non-snoopable address region. Alternatively, from a Home Node to any address region to obtain a copy of the addressed data. See Table B2.6 for use DMT, Order field, and ExpCompAck values.

**ReadNoSnpSep**

Read request from a Home Node to Subordinate Node, requesting the Completer to send only a data response. Used when separate completion and data responses are used to complete the read transaction.

**ReadOnce**

Read request to a Snoopable address region to obtain a snapshot of the coherent data.

**ReadOnceCleanInvalid**

Read request to a Snoopable address region to obtain a snapshot of the coherent data. It is recommended, but not required, that other cached copies of the cache line are cleaned and invalidated. If a Dirty copy is invalidated, it must be written back to memory.

> **_NOTE:_** ReadOnceCleanInvalid is used instead of ReadOnce or ReadOnceMakeInvalid where the application determines that the data is still Valid, but is not used in the near future.
>
> Use of ReadOnceCleanInvalid by an application improves cache efficiency by reducing cache pollution.

The following should be considered when using ReadOnceCleanInvalid:

- The clean and invalidation in the ReadOnceCleanInvalid transaction is a hint. Completion of the transaction does not guarantee the cleaning or removal of all cached copies, therefore it cannot be used as a replacement for a CMO.
- Use of the transaction can cause the deallocation of a cache line and therefore caution is needed if the transaction could target the same cache line that other agents in the system are using for Exclusive accesses.

**ReadOnceMakeInvalid**

Read request to a Snoopable address region to obtain a snapshot of the coherent data. It is recommended, but not required, that other cached copies of the cache line are invalidated. If a Dirty copy is invalidated, the cache line does not need to be written back to memory. All cached copies must be invalidated if the invalidation hint is accepted and a Dirty copy is not written back to memory.

> **_NOTE:_** ReadOnceMakeInvalid is used in preference to ReadOnce or ReadOnceCleanInvalid to obtain a snapshot of a data value when the application determines that the cached data is not going to be used again.
>
> The application can free up the caches and also, by discarding Dirty data, avoid an unnecessary WriteBack to memory.

The following should be considered when using ReadOnceMakeInvalid:

- The invalidation in the ReadOnceMakeInvalid transaction is a hint. Completion of the transaction does not guarantee removal of all cached copies. The invalidation hint cannot be used as a replacement for a CMO.
- Use of the transaction can cause the deallocation of a cache line and therefore caution is needed if the transactions could target the same cache line that other agents in the system are using for Exclusive accesses.
- The use of the ReadOnceMakeInvalid transaction can cause the loss of a Dirty cache line. Use of this transaction must be strictly limited to scenarios where the loss of a Dirty cache line is known and