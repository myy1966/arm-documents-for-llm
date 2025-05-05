            - **Alt 3a2. Combined response from Home**

                The Home returns a combined data request and completion response, CompDBIDResp, to the Requester.

        - The Requester has several alternatives to send write data depending on whether the transaction requires a completion acknowledge.

            - **Alt 3b1. No CompAck required**

                The Requester sends write data, NonCopyBackWriteData, or a write cancellation, WriteDataCancel, to the Home. The Requester must only send this after receiving DBIDResp, DBIDRespOrd, or CompDBIDResp.

            - **Alt 3b2. CompAck required**

                A completion acknowledge response, CompAck, is required. The Requester has two alternatives to send write data and CompAck to the Home.

                - **Alt 3b2a. Separate responses from Requester**

                    The Requester does both the following:

                    - Sends write data, NonCopyBackWriteData, or a write cancellation, WriteDataCancel, to the Home.

                        The Requester must only send this after receiving DBIDResp, DBIDRespOrd, or CompDBIDResp.

                    - Sends a completion acknowledge, CompAck, to the Home. The Requester must only send this after it has received DBIDResp, DBIDRespOrd, CompDBIDResp, or Comp. It is permitted, but not required, to wait for DBIDResp or DBIDRespOrd before sending CompAck. It is not permitted to wait for Comp, CompCMO, or Persist before sending CompAck.

                - **Alt 3b2b. Combined response from Requester**

                    The Requester sends a combined write data and completion acknowledge, NonCopyBackWriteDataCompAck, to the Home. The Requester must only send this after it has received DBIDResp, DBIDRespOrd, or CompDBIDResp. It is not permitted to wait for Comp before sending NonCopyBackWriteDataCompAck if DBIDResp or DBIDRespOrd have been received. It is not permitted to wait for CompCMO or Persist before sending NonCopyBackWriteDataCompAck.

        - The Home has several alternatives to complete the remainder of the transaction.

            - **Alt 3c1. Combined Write without DWT to Subordinate**

                - The Home sends a Combined Write without DWT to the Subordinate.
                - The Subordinate has two alternatives to request write data.

                    - **Alt 3c1a. Separate responses from Subordinate**

                        The Subordinate does both the following:

                        - Returns a data request, DBIDResp, to the Home.
                        - Returns a completion response, Comp, to the Home. It is permitted, but not required, to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, before returning Comp.

                    - **Alt 3c1b. Combined response from Subordinate**

                        The Subordinate returns a combined data request and completion response, CompDBIDResp, to the Home.

                - The Home sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate. The Home must only send this after receiving DBIDResp or CompDBIDResp.