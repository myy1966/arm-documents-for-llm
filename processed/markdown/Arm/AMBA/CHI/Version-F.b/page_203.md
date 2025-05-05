- WriteNoSnpFull:

    - WriteNoSnpFullCleanInv
    - WriteNoSnpFullCleanSh
    - WriteNoSnpFullCleanShPerSep
    - WriteNoSnpFullCleanInvPoPA

- WriteNoSnpPtl:

    - WriteNoSnpPtlCleanInv
    - WriteNoSnpPtlCleanSh
    - WriteNoSnpPtlCleanShPerSep
    - WriteNoSnpPtlCleanInvPoPA

- WriteUniqueFull:

    - WriteUniqueFullCleanSh
    - WriteUniqueFullCleanShPerSep

- WriteUniquePtl:

    - WriteUniquePtlCleanSh
    - WriteUniquePtlCleanShPerSep

- WriteBackFull:

    - WriteBackFullCleanInv
    - WriteBackFullCleanSh
    - WriteBackFullCleanShPerSep
    - WriteBackFullCleanInvPoPA

- WriteCleanFull:

    - WriteCleanFullCleanSh
    - WriteCleanFullCleanShPerSep

#### B4.2.4.1 Characteristics

A Combined Write request is permitted for both CopyBack and Immediate writes.

All permitted behaviors of the Combined Write request are the same as if the write and CMO are sent separately, except that:

- WriteNoSnp(Excl) is not permitted to be combined with a CMO.
- TagOp setting of Match is not permitted in Write*CMO.

A Home receiving a Combined Write request from a Request Node is permitted to forward the Combined Write to the Subordinate Node if both the write and the CMO or PCMO in the request need to be sent downstream. The Home is also permitted to use DWT for such a Write request if the write from the Request Node is an Immediate write and ExpCompAck is set to 0.

Where an uncombined CMO from a Request Node results in the cache line being evicted from a cache at the Home or a Dirty copy is passed in a Snoop response, the CMO propagated to the Subordinate can be combined with the write back to the Subordinate.

The receiver of a Combined Write request is permitted to separate the write and the CMO request and process them separately. In such a case, the CMO request must be ordered behind the write. Once the requests are separated, the Completer is permitted to interleave requests to the same address between the write and the CMO transaction.

The Size field value in a combined request corresponds to the size of Data in the Write request. The CMO is always on a 64-byte granularity.