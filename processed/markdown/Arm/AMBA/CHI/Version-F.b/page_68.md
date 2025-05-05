- The transaction starts with the Requester issuing a Combined Write and CMO request to the Home. The Combined Immediate Write and CMO transactions are:

    - WriteNoSnpPtlCleanInv
    - WriteNoSnpPtlCleanSh
    - WriteNoSnpFullCleanInv
    - WriteNoSnpFullCleanSh
    - WriteUniquePtlCleanSh
    - WriteUniqueFullCleanSh
    - WriteNoSnpPtlCleanInvPoPA
    - WriteNoSnpFullCleanInvPoPA

    Snoop requests that are generated to complete these transactions are considered as independent transactions from the Home and are not shown in this flow. Write requests that are generated to downstream Subordinates, which are not part of the DWT flow, are considered as independent transactions and are not shown in this flow. Also, CMO requests that only return responses to the Home and are generated to downstream Subordinates are considered independent transactions. See B2.3.9 Home Initiated transactions for more details on independent transactions from the Home. See B2.3.9.2 Home to Subordinate Write transactions for more details on independent Combined Write and CMO transactions from the Home.

    The request contains the following fields which affect the transaction flow:

    - Opcode
    - ExpCompAck

    > **_NOTE:_** A TagOp value of Match is not permitted in a Combined Immediate Write and CMO transaction, therefore no TagMatch responses are permitted and the TagOp field does not affect the transaction flow.

- The Home has three alternatives to choose from to complete the transaction:

    - Combined Write to Subordinate with DWT.
    - Non-combined Write to Subordinate with DWT.
    - Without DWT.

    The three approaches are described in the alternatives 1-3.

- The remainder of the transaction flow depends on whether the original request required a completion acknowledge, as determined by the ExpCompAck.

    1. **Combined Write to Subordinate with DWT**

        The Home uses a Combined Write with DWT.

        - The Home sends a downstream combined write request with DoDWT = 1 to the Subordinate.
        - The Subordinate returns a data request, DBIDResp, to the Requester.
        - The Requester sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate. The Requester must only send this after receiving DBIDResp.
        - The Subordinate returns a completion response, Comp, to the Home. It is permitted, but not required, for the Subordinate to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, from the Requester before returning Comp to the Home.
        - The Home returns a completion response, Comp, to the Requester. It is permitted, but not required, for the Home to wait for Comp from the Subordinate before returning Comp to the Requester.
        - The Subordinate returns a CMO completion response, CompCMO, to the Home. It is permitted, but not required, for the Subordinate to wait for write data from the Requester before returning CompCMO to the Home.