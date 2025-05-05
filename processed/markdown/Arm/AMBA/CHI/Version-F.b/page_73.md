        - The Home returns a CMO completion response, CompCMO, to the Requester. It is permitted, but not required, for the Home to wait for Comp or CompCMO from the Subordinate before returning CompCMO to the Requester. If there is an observer downstream of the Home, the Home must wait for the CompCMO response from the Subordinate before returning CompCMO to the Requester.
        - The Subordinate returns a persist response, Persist, to the Requester. It is permitted, but not required, to wait for write data before returning Persist.

    2. **Non-combined Write to Subordinate with DWT**

        - The Home sends a downstream Non-combined Write request, WriteNoSnpPtl or WriteNoSnpFull, with DoDWT = 1 to the Subordinate.
        - The Subordinate returns a data request, DBIDResp, to the Requester.
        - The Requester sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate. The Requester must only send this after receiving DBIDResp.
        - The Subordinate returns a completion response, Comp, to the Home. It is permitted, but not required, for the Subordinate to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, from the Requester before returning Comp to the Home.
        - The Home returns a completion response, Comp, to the Requester. It is permitted, but not required, for the Home to wait for Comp from the Subordinate before returning Comp to the Requester.
        - The Home has two alternatives to send the CMO responses to the Requester.

            - **Alt 2a. Persist CMO to Subordinate**

                - The Home sends a downstream request, CleanSharedPersistSep, to the Subordinate.
                - The Subordinate returns a completion response, Comp, to the Home.
                - The Home returns a CMO completion response, CompCMO, to the Requester. If there is an observer downstream of the Home, the Home must wait for the Comp response from the Subordinate before returning CompCMO to the Requester.
                - The Subordinate returns a persist response, Persist, to the Requester.

            - **Alt 2b. No CMO to Subordinate as part of transaction**

                The Home sends all the CMO responses to the Requester. All CMO responses can be sent from the Home in two alternative ways.

                - **Alt 2b1. Separate responses from Home**

                    The Home does both the following:

                    - Returns a CMO completion response, CompCMO, to the Requester.
                    - Returns a persist response, Persist, to the Requester.

                - **Alt 2b2. Combined response from Home**

                    The Home returns a combined completion and persist response, CompPersist, to the Requester.

    3. **No DWT**

        The Home does not use DWT.

        - The Home has two alternatives to request write data.

            - **Alt 3a1. Separate responses from Home**

                The Home does both of the following:

                - Returns a data request, DBIDResp or DBIDRespOrd, to the Requester.
                - Returns a completion response, Comp, to the Requester. It is permitted, but not required, to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, before returning Comp.