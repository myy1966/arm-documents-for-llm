                    - Returns a data request, DBIDResp, to the Home.
                    - Returns a completion response, Comp, to the Home. It is permitted, but not required, to wait for write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, before returning Comp.

                - **Alt 2b2b. Combined response**

                    The Subordinate returns a combined data request and completion response, CompDBIDResp, to the Home.

            - The Home sends write data, NonCopyBackWriteData, or a cancellation, WriteDataCancel, to the Subordinate.
            - The Home must only send this after receiving DBIDResp or CompDBIDResp.
            - The Subordinate returns a CMO completion response, CompCMO, to the Home. It is permitted, but not required, to wait for write data before returning CompCMO.
            - The Home returns a CMO completion response, CompCMO, to the Requester. It is permitted, but not required, for the Home to wait for CompCMO from the Subordinate before returning CompCMO to the Requester.
            - The Subordinate returns a persist response, Persist, to the Requester. It is permitted, but not required, to wait for write data before returning Persist.

        - **Alt 2b3. Only CMO transaction to Subordinate**

            When a persist CMO is sent to the Subordinate and the Persist response is returned to the Requester, the following happens:

            - The Home sends a downstream request, CleanSharedPersistSep, to the Subordinate. Typically, this alternative would only be used where a write to the Subordinate has been previously sent as an independent transaction or the write has been canceled.
            - The Subordinate returns a completion response, Comp, to the Home.
            - The Home returns a completion response, CompCMO, to the Requester. If there is an observer downstream of the Home, Home must wait for the Comp response from the Subordinate before returning CompCMO to the Requester.
            - The Subordinate returns a persist response, Persist, to the Requester.

### B2.3.3 Atomic transactions

Figure B2.9 shows the possible transaction flows for an Atomic transaction.