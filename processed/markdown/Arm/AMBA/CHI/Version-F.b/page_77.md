There are two possible sequences for Combined CopyBack and CMO transactions.

Write requests that are generated to downstream Subordinates and not part of the DWT or persist flow. These write requests are considered independent transactions and are not shown in this flow. CMO requests that are generated to downstream Subordinates, which only return responses to the Home, are considered as independent transactions and are not shown in this flow. See B2.3.9 Home Initiated transactions for more details on independent transactions from the Home. See B2.3.9.4 Home to Subordinate Combined Write and CMO transactions for more details on independent Combined Write and CMO transactions from the Home.

The request contains the following field which affects the transaction flow:

- Opcode
- CAH

1. **Without Persist**

    The Combined CopyBack Write and CMO transactions without persist are:

    - WriteBackFullCleanInv
    - WriteBackFullCleanSh
    - WriteCleanFullCleanSh
    - WriteBackFullCleanInvPoPA

    The Requester issues a Combined CopyBack Write and CMO request without Persist response.

    - The Requester issues a request to the Home.

        - **Alt 1a. CopyAtHome request**

            The CAH bit value in the request is set to 1.

            The Home has two alternative responses to return to the Requester.

            - **Alt 1a1. Without data transfer**

                - The Home returns a completion response, Comp, to the Requester to avoid the data transfer.
                - The Requester sends a completion acknowledge, CompAck. The Requester must send this regardless of the ExpCompAck value in the original request and only after receiving the Comp response.

            - **Alt 1a2. With data transfer**

                - The Home returns a combined data request and completion response, CompDBIDResp, to the Requester.
                - The Requester sends write data, CopyBackWriteData, to the Home. The Requester must only send this after receiving CompDBIDResp.

        - **Alt 1b. No CopyAtHome request**

            The CAH bit value in the request is set to 0.

            - The Home sends a combined data request and completion response, CompDBIDResp, to the Requester.
            - The Requester sends write data, CopyBackWriteData, to the Home. The Requester must only send this after receiving CompDBIDResp.

    - The Home returns a CMO completion response, CompCMO, to the Requester. It is permitted, but not required, to wait for CopyBackWriteData or CompAck before returning CompCMO.

2. **With Persist**

    The Combined CopyBack write and CMO transactions are:

    - WriteBackFullCleanShPerSep
    - WriteCleanFullCleanShPerSep