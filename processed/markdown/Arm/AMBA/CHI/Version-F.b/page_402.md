    - Transfer: Clean tags must be returned. TU bits are inapplicable and must be set to 0.
    - Update: All TU bits must be asserted.
    - Match: Not permitted.

- For WriteBackPtl with TagOp:

    - Transfer: Not permitted.
    - Update: Not permitted.
    - Match: Not permitted.

- For WriteNoSnpFull with TagOp:

    - Transfer: TU bits are inapplicable and must be set to 0. Clean tag transfer is permitted from the Request Node to the Home Node as well as the Home Node to the Subordinate Node.
    - Update: All TU bits must be asserted.
    - Match: TU bits are inapplicable and must be set to 0.

- For WriteNoSnpDef with TagOp:

    - Transfer: Not permitted.
    - Update: Not permitted.
    - Match: Not permitted.

- For WriteUniqueFull and WriteUniqueFullStash with TagOp:

    - Transfer: Not permitted.
    - Update: All TU bits must be asserted.
    - Match: TU bits are inapplicable and must be set to 0.

- For WriteNoSnpPtl, WriteUniquePtl and WriteUniquePtlStash with TagOp:

    - Transfer: Not permitted.
    - Update: Any combination of TU and BE bits, including none or all, can be asserted.
    - Match: TU bits are inapplicable and must be set to 0. Tag Match must be performed for only those tags that have at least one corresponding BE bit asserted. A Tag Match must not be performed when all BE bits are set to 0.

- For WriteEvictFull, WriteEvictOrEvict and with TagOp:

    - Transfer: Clean tags must be returned. TU bits are inapplicable and must be set to 0.
    - Update: Not permitted.
    - Match: Not permitted.

- For WriteNoSnpZero and WriteUniqueZero only TagOp Invalid is permitted.

For a Write request with a TagOp of Match the tags within the size wrap boundary can take any value, and the tags outside of size are inapplicable and can also take any value.

In the WriteDataCancel Write data response, irrespective of the TagOp value in the Write request, the MTE fields are inapplicable and must be set to 0.

In Write data, with TagOp Invalid, all the TU bits and all the Tag bits must be set to 0.