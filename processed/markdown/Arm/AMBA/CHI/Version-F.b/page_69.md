        - The Home returns a CMO completion response, CompCMO, to the Requester. It is permitted, but not required, for the Home to wait for Comp or CompCMO from the Subordinate before returning CompCMO to the Requester. If there is an observer downstream of the Home, the Home must wait for the CompCMO response from the Subordinate before returning CompCMO to the Requester.

    2. **Non-combined Write to Subordinate with DWT**

        The Home uses a Non-combined Write with DWT.

        - The Home sends a downstream WriteNoSnpPtl or WriteNoSnpFull, with DoDWT = 1 to the Subordinate.
        - The Subordinate returns a data request, DBIDResp, to the Requester.
        - The Requester sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate. The Requester must only send this after receiving DBIDResp.
        - The Subordinate returns a completion response, Comp, to the Home. It is permitted, but not required, for the Subordinate to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, from the Requester before returning Comp to the Home.
        - The Home returns a completion response, Comp, to the Requester. It is permitted, but not required, for the Home to wait for Comp from the Subordinate before returning Comp to the Requester.
        - The Home returns a CMO completion response, CompCMO, to the Requester. It is permitted, but not required, for the Home to wait for Comp from the Subordinate before returning CompCMO to the Requester.

    3. **No DWT**

        - The Home does not use DWT.
        - The Home has two alternatives to request write data.

            - **Alt 3a1. Separate responses from Home**

                The Home does both the following:

                - Returns a data request, DBIDResp or DBIDRespOrd, to the Requester.
                - Returns a completion response, Comp, to the Requester. It is permitted, but not required, to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, before returning Comp.

            - **Alt 3a2. Combined response from Home**

                The Home returns a combined data request and completion response, CompDBIDResp, to the Requester.

        - The Requester has several alternatives to send write data depending on whether the transaction requires a completion acknowledge.

            - **Alt 3b1. No CompAck required**

                A completion acknowledge, CompAck, is not required and the Requester sends write data, NonCopyBackWriteData, or a write cancellation, WriteDataCancel, to the Home. The Requester must only send this after receiving DBIDResp, DBIDRespOrd, or CompDBIDResp.

            - **Alt 3b2. CompAck required**

                A completion acknowledge is required. The Requester has two alternatives to send write data and completion acknowledge to the Home.

                - **Alt 3b2a. Separate response from Requester**

                    The Requester does both the following:

                    - Sends write data, NonCopyBackWriteData, or a write cancellation, WriteDataCancel, to the Home. The Requester must only send this after receiving DBIDResp, DBIDRespOrd, or CompDBIDResp.