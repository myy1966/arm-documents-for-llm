                - The Subordinate returns a CMO completion response, CompCMO, to the Home. It is permitted, but not required, to wait for write data before returning CompCMO.
                - The Home returns a CMO completion response, CompCMO, to the Requester. It is permitted, but not required, for the Home to wait for CompCMO from the Subordinate before returning CompCMO to the Requester.
                - The Subordinate returns a persist response, Persist, to the Requester. It is permitted, but not required, to wait for write data before returning Persist.

            - **Alt 3c2. All CMO transactions from Home**

                The Home has two alternatives to send all CMO responses to the Requester.

                - **Alt 3c2a. Separate responses from Home**

                    The Home does both the following:

                    - Returns a CMO completion response, CompCMO, to the Requester.
                    - Returns a persist response, Persist, to the Requester.

                - **Alt 3c2b. Combined response from Home**

                    The Home returns a combined completion and persist response, CompPersist, to the Requester.

            - **Alt 3c3. Only CMO transactions to Subordinate**

                - The Home sends a downstream request, CleanSharedPersistSep, to the Subordinate. Typically, this alternative would only be used where a write to the Subordinate has been previously sent as an independent transaction.
                - The Subordinate returns a completion response, Comp, to the Home.
                - The Home returns a CMO completion response, CompCMO, to the Requester. If there is an observer downstream of the Home, the Home must wait for the Comp response from the Subordinate before returning CompCMO to the Requester.
                - The Subordinate returns a persist response, Persist, to the Requester.

#### B2.3.2.6 Combined CopyBack Write and CMO

Figure B2.8 shows the possible transaction flows for a Combined CopyBack Write and CMO transaction.