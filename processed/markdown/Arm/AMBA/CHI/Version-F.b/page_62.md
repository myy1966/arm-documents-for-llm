                - Returns a completion response, Comp, to the Requester. It is permitted, but not required, to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, before returning Comp.

            - **Alt 2a2. Combined response from the Home**

                The Home returns a combined data request and completion response, CompDBIDResp, to the Requester.

        - The Requester sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Home. The Requester must only send this after receiving DBIDResp, DBIDRespOrd, or CompDBIDResp.
        - Optionally, when the request requires a TagMatch response, the Home has two alternatives.

            - **Alt 2b1. TagMatch from Home**

                The Home returns a tag match response, TagMatch, to the Requester. It is permitted, but not required, to wait for write data before returning TagMatch.

            - **Alt 2b2. TagMatch from Subordinate**

                - The Home sends a downstream write request, WriteNoSnpPtl or WriteNoSnpFull, with DoDWT = 0 to the Subordinate. The Subordinate has two alternatives to send return data request and completion response to the Home.

                    - **Alt 2b2a. Separate responses from the Subordinate**

                        The Subordinate does both the following:

                        - Returns a data request, DBIDResp, to the Home.
                        - Returns a completion response, Comp, to the Home.

                            It is permitted, but not required, for the Subordinate to wait for write data from the Home before returning Comp to the Home.

                    - **Alt 2b2b. Combined response from the Subordinate**

                        The Subordinate returns a combined data request and completion response, CompDBIDResp, to the Home.

                - The Home sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate. The Home must only send this after receiving DBIDResp or CompDBIDResp.
                - The Subordinate returns a tag match response, TagMatch, to the Requester. It is permitted, but not required, to wait for write data before returning TagMatch.

    3. **No DWT, with CompAck**

        The Home does not use DWT for a request that does require a completion acknowledge, CompAck.

        - The Home has two alternatives to return the completion response and the data request response to the Requester.

            - **Alt 3a1. Separate response from the Home**

                The Home does both the following:

                - Returns a data request, DBIDResp or DBIDRespOrd, to the Requester.
                - Returns a completion response, Comp, to the Requester.

                It is permitted, but not required, to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, before returning Comp.

            - **Alt 3a2. Combined response from the Home**

                The Home returns a combined data request and completion response, CompDBIDResp, to the Requester.