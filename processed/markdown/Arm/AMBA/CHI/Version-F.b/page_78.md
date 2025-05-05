    The Requester issues a Combined CopyBack Write and CMO request with Persist response.

    - The Requester issues a request to the Home.

        - **Alt 2a1. CopyAtHome request**

            The CAH bit value in the request is set to 1. The Home has two alternative responses to return to the Requester.

            - **Alt 2a1a. Without data transfer**

                - The Home returns a completion response, Comp, to the Requester to avoid the data transfer.
                - The Requester sends a completion acknowledge, CompAck. The Requester must send this regardless of the ExpCompAck value in the original request and only after receiving the Comp response.

            - **Alt 2a1b. With data transfer**

                - The Home returns a combined data request and completion response, CompDBIDResp, to the Requester.
                - The Requester sends write data, CopyBackWriteData, to the Home. The Requester must only send this after receiving CompDBIDResp.

        - **Alt 2a2. No CopyAtHome request**

            The CAH bit value in the request is set to 0.

            - The Home sends a combined data request and completion response, CompDBIDResp, to the Requester.
            -  The Requester sends write data, CopyBackWriteData, to the Home. The Requester must only send this after receiving CompDBIDResp.

        The Home has three alternatives to complete the transaction, with the persist response either coming from the Home or from the Subordinate.

        - **Alt 2b1. Persist from Home**

            The Home has two alternatives to send the CMO completion response and persist response. It is permitted, but not required, for the Home to wait for CopyBackWriteData or CompAck before returning CompCMO, Persist, or CompPersist.

            - **Alt 2b1a. Separate response from Home**

                - Returns a CMO completion response, CompCMO, to the Requester.
                - Returns a persist response, Persist, to the Requester.

            - **Alt 2b2b. Combined response from Home**

                The Home returns a combined CMO completion response and persist response, CompPersist, to the Requester.

        - **Alt 2b2. Persist from Subordinate**

            When a Combined Write is sent to the Subordinate and the Persist response is returned to the Requester, the following happens:

            - The Home sends a downstream write request, WriteNoSnpPtlCleanShPerSep or WriteNoSnpFullCleanShPerSep, to the Subordinate.
            - It is permitted, but not required, for the Home to wait for CopyBackWriteData or CompAck before sending the downstream write request.
            - The Subordinate has two alternatives to return the completion response and the data request response to the Home.

                - **Alt 2b2a. Separate response**

                    The Subordinate does both the following: