    - The Stashee has two alternatives to respond to the stash snoop request.

    - **Alt 2a. No DataPull**

        Not request a data pull.

    - **Alt 2b. DataPull**

        Request a data pull.

        The completion of a request with data pull is identical to the completion of an Allocating Read transaction, see B2.3.1.1 Allocating Read for details.

    The transaction completes with the Home returning a completion response, Comp, to the original Requester.

    It is permitted, but not required, to wait for the stash transaction to complete before the Comp response is returned.

3. **Independent Stash with StashDone response**

    An independent Stash with a StashDone response starts the transaction. The independent Stash requests with a StashDone response are:

    - StashOnceSepUnique
    - StashOnceSepShared

    The Home can optionally send a stash snoop request, SnpStashUnique or SnpStashShared, to the Stashee. Typically the Home sends SnpStashUnique when the original request is StashOnceSepUnique and SnpStashShared when the original request is StashOnceSepShared.

    - The Stashee has two alternatives to respond to the stash snoop request.

        - **Alt 3a1. No DataPull**

            Not request a data pull.

        - **Alt 3a2. DataPull**

            Request a data pull.

            The completion of a request with data pull is identical to the completion of an Allocating Read transaction, see B2.3.1.1 Allocating Read for details.

    The Home has two alternatives to complete the transaction.

    - **Alt 3b1. Separate responses from Home**

        The Home does both the following:

        - Returns a completion response, Comp, to the Requester.
        - Returns a stash done response, StashDone, to the Requester.

    - **Alt 3b2. Combined response from Home**

        The Home returns a combined completion and stash done response, CompStashDone, to the Requester.

### B2.3.5 Dataless transactions

Figure B2.11 shows the transaction flow for a Dataless transaction.