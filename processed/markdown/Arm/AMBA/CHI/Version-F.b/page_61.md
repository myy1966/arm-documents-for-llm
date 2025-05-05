The sequence for Immediate Write transactions is:

- The transaction starts with the Requester issuing an Immediate Write request to the Home. The Immediate Write transactions are:

    - WriteNoSnpPtl
    - WriteNoSnpFull
    - WriteNoSnpDef
    - WriteUniquePtl
    - WriteUniqueFull
    - WriteUniquePtlStash
    - WriteUniqueFullStash

    Snoop requests that are generated to complete these transactions are considered independent transactions from the Home and are not shown in this flow. Write requests that are generated to downstream Subordinates, which are not part of the DWT flow, are considered as independent transactions and are not shown in this flow. See B2.3.9 Home Initiated transactions for more details of independent transactions from the Home. Stash snoops that are generated to complete the WriteUniquePtlStash or WriteUniqueFullStash transactions are described in the later section on Stash transactions, see B2.3.4 Stash transactions.

    The request contains the following fields which affect the transaction flow:

    - ExpCompAck
    - TagOp

- The Home can choose to complete the transaction using DWT or without DWT. The remainder of the transaction flow depends on whether the original request requires a completion acknowledge response, as determined by the ExpCompAck field. The combinations are described in alternatives 1-3:

    1. **DWT**

        The Home uses DWT.

        - The Home sends a downstream write request, WriteNoSnpPtl, WriteNoSnpFull, or WriteNoSnpDef, with DoDWT = 1 to the Subordinate.
        - The Subordinate returns a data request, DBIDResp, to the Requester.
        - The Requester sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate. The Requester must only send this after receiving DBIDResp.
        - The Subordinate returns a completion response, Comp, to the Home. It is permitted, but not required, for the Subordinate to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, from the Requester before returning Comp to the Home.
        - The Home returns a completion response, Comp, to the Requester. It is permitted, but not required, for the Home to wait for Comp from the Subordinate before returning Comp to the Requester.
        - Optionally, when the request requires a TagMatch response, the Subordinate returns a tag match response, TagMatch, to the Requester. It is permitted, but not required, to wait for write data before returning TagMatch.

    2. **No DWT, no CompAck**

        The Home does not use DWT for a request that does not require a completion acknowledge, CompAck.

        - The Home has two alternatives to send the completion response and the data request response to the Requester.

            - **Alt 2a1. Separate responses from the Home**

                The Home does both the following:

                - Returns a data request, DBIDResp or DBIDRespOrd, to the Requester.