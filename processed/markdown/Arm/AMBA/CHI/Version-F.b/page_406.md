## B12.9 Snoop requests

This section describes the permitted use by Home of the following snoop types:

- B12.9.1 Non-forwarding snoops
- B12.9.2 Forwarding snoops
- B12.9.3 Stash snoops

### B12.9.1 Non-forwarding snoops

Home can use any applicable Non-forwarding snoop when tags are needed by the request. If the Snoop response returns data to Home but not tags, the Home is responsible for obtaining tags before returning the Data response to the Requester.

A Home in response to WriteUniqueFull, WriteUniqueFullStash, MakeUnique, and MakeInvalid must not use the SnpMakeInvalid snoop request unless either:

- The transaction is WriteUniqueFull, WriteUniqueFullStash, or MakeUnique with a TagOp value of Update.
- The Home can determine that the Snoopee does not hold Dirty tags.

> **_NOTE:_** By sending a ReadUnique with TagOp Fetch, a Requester is indicating its willingness to update the full cache line but not the tags. Home must not use SnpMakeInvalid in response to such a request, to avoid losing modified tags at the Snoopee.

### B12.9.2 Forwarding snoops

The use by Home of the Forwarding snoop is permitted only if the request does not need to fetch tags. A Forwarding snoop is permitted to be sent even when the Snoopee has Valid tags. If the Snoopee has Dirty tags when responding to a Forwarding snoop, Dirty tags must not be forwarded to the Requester nor split dirtiness or uniqueness of tags and data.

A Snoopee is always permitted to forward Clean tags to the Requester.

When tags are Clean, the Snoopee must follow the same data transfer rules as in the Non-MTE case.

When tags are Dirty, the Snoopee must follow the rules:

- For the invalidating Forwarding snoop SnpUniqueFwd and SnpPreferUniqueFwd handled as an invalidating snoop:

    - Must not forward data to the Requester.
    - Must return data and tags to the Home.

- For the Non-invalidating Forwarding snoops SnpCleanFwd, SnpSharedFwd, SnpNotSharedDirtyFwd, SnpPreferUniqueFwd handled as a non-invalidating snoop:

    - Must treat the snoop as SnpCleanFwd.

        > **_NOTE:_** Same as SnpNotSharedDirtyFwd.

- For SnpOnceFwd: