        - The Requester has two alternatives to send write data and completion acknowledge to the Home.

            - **Alt 3b1. Separate response from the Requester**

                The Requester does both the following:

                - Sends write data, NonCopyBackWriteData, or a write cancellation, WriteDataCancel, to the Home.
                - The Requester must only send this after receiving DBIDResp, DBIDRespOrd, or CompDBIDResp.
                - Sends a completion acknowledge, CompAck, to the Home. The Requester must only send this after it has received DBIDResp, DBIDRespOrd, CompDBIDResp, or Comp. It is permitted, but not required, to wait for DBIDResp or DBIDRespOrd before sending CompAck. It is not permitted to wait for Comp before sending CompAck. It is permitted, but not expected, to wait for TagMatch before returning CompAck.

            - **Alt 3b2. Combined response from the Requester**

                The Requester sends a combined write data and completion acknowledge, NonCopyBackWriteDataCompAck, to the Home.

                The Requester must only send this after it has received DBIDResp, DBIDRespOrd, or CompDBIDResp.

                It is not permitted to wait for Comp before sending NCBWRrDataCompAck if DBIDResp or DBIDRespOrd have been received.

        - Optionally, when the request requires a TagMatch response, the Home has two alternatives to return the response.

            - **Alt 3c1. TagMatch from Home**

                The Home returns a tag match response, TagMatch, to the Requester. It is permitted, but not required, to wait for write data before returning TagMatch.

            - **Alt 3c2. TagMatch from Subordinate**

                - The Home sends a downstream write request, WriteNoSnpPtl or WriteNoSnpFull, with DoDWT = 0 to the Subordinate. The Subordinate has two alternatives to return data request and completion response to the Home.

                    - **Alt 3c2a. Separate responses from Subordinate**

                        The Subordinate does both the following:

                        - Returns a data request, DBIDResp, to the Home.
                        - Returns a completion response, Comp, to the Home. It is permitted, but not required, for the Subordinate to wait for write data before sending Comp to the Home.

                    - **Alt 3c2b. Combined response from Subordinate**

                        The Subordinate returns a combined data request and completion response, CompDBIDResp, to the Home.

                - The Home sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate.

                    The Home must only send this after receiving DBIDResp or CompDBIDResp.

                - The Subordinate returns a tag match response, TagMatch, to the Requester. It is permitted, but not required, to wait for write data before returning TagMatch.

The Completer of a Write transaction is permitted to return a Comp response when a WriteDataCancel response is received without dependency on either the processing of the write request or the completion of any snoops sent due to the write.