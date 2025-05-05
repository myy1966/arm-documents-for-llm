An early response from an intermediate component can stop the original Requester observing a valid Defer response from the final endpoint, reducing the effectiveness of the deferrable write transaction.

- CMOtransactions.
- Atomic transactions.
- Must be asserted in any:

    - Read transaction that is not a ReadNoSnp, ReadNoSnpSep, or CMO transaction.
    - Dataless transaction that is not a CMO transaction.
    - Write transaction that is not a WriteNoSnp or WriteNoSnpDef transaction.

- Is inapplicable and:

    - Must be set to 0 in the DVMOp or PCrdReturn transactions.
    - Can take any value in the PrefetchTgt transaction.

#### B2.7.3.2 Device

Device attribute indicates if the memory type is either Device or Normal.

##### B2.7.3.2.1 Device memory type

Device memory type must be used for locations that exhibit side-effects. Use of Device memory type for locations that do not exhibit side-effects is permitted.

The requirements for a transaction to a Device type memory location are:

- A Read transaction must not read more data than requested.
- Prefetching from a Device memory location is not permitted.
- A read must get its data from the endpoint. A read must not be forwarded data from a write to the same address location that completed at an intermediate point.
- Combining requests to different locations into one request, or combining different requests to the same location into one request, is not permitted.
- Writes must not be merged.
- Writes to Device memory that obtain completion from an intermediate point must make the write data visible to the endpoint in a timely manner.

Accesses to Device memory must use the following types, exclusive variants are permitted:

- Read accesses to a Device memory location must use ReadNoSnp.
- Write accesses to a Device memory location must use WriteNoSnpPtl, WriteNoSnpFull, WriteNoSnpZero, or WriteNoSnpDef.
- CMOtransactions are permitted to Device memory locations.
- Atomic transactions are permitted to Device memory locations.
- The PrefetchTgt transaction is not permitted to Device memory locations. The MemAttr field is inapplicable and can take any value in the PrefetchTgt transaction.

##### B2.7.3.2.2 Normal memory type

Normal memory type is appropriate for memory locations that do not exhibit side-effects.

Accesses to Normal memory do not have the same restrictions regarding prefetching or forwarding as Device type memory:

- A Read transaction that has EWA asserted can obtain read data from a Write transaction that has sent its completion from an intermediate point and is to the same address location.