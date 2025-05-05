There are three possible sequences for Stash transactions.

The following can affect transaction flow:

- The Home is permitted to ignore the Stash request and not perform any stash snoops.
- The Stashee is permitted to ignore the Stash request and not request a data pull to complete the transaction.
- StashOnceSepUnique and StashOnceSepShared can have a separate StashDone response or combined CompStashDone response.

1. **Write with Stash Hint**

    A write with Stash hint starts the transaction. The write with Stash hint requests are:

    - WriteUniquePtlStash
    - WriteUniqueFullStash

    The WriteUnique uses the same transaction flows as an Immediate Write, see B2.3.2.1 Immediate Write for details.

    The Home can optionally send a stash snoop request.

    - **Alt 1a. SnpUniqueStash**

        - The Home sends SnpUniqueStash to the Stashee. Typically the Home sends SnpUniqueStash for a partial line write. Other snoops, including other
        - stash snoops, are permitted.
        - The Stashee has two alternatives to respond to the stash snoop request.

        - **Alt 1a1. No DataPull**

            Not request a data pull.

        - **Alt 1a2. DataPull**

            Request a data pull.

            The completion of a request with data pull is identical to the completion of an Allocating Read transaction, see B2.3.1.1 Allocating Read for details.

    - **Alt 1b. Other stash snoops**

        - Send SnpMakeInvalidStash, SnpStashShared, or SnpStashUnique, to the Stashee. Typically, the Home sends SnpMakeInvalidStash for a full line write. Other snoops, including other stash snoops, are permitted.
        - The Stashee has two alternatives to respond to the stash snoop request.

        - **Alt 1b1. No DataPull**

            Not request a data pull

        - **Alt 1b2. DataPull**

            Request a data pull.

            The completion of a request with data pull is identical to the completion of an Allocating Read transaction, see B2.3.1.1 Allocating Read for details.

2. **Independent Stash without StashDone response**

    An independent Stash without a StashDone response starts the transaction. The independent Stash requests without a StashDone response are:

    - StashOnceUnique
    - StashOnceShared

    The Home can optionally send a stash snoop request, SnpStashUnique or SnpStashShared, to the Stashee. Typically the Home sends SnpStashUnique when the original request is StashOnceUnique and SnpStashShared when the original request is StashOnceShared.