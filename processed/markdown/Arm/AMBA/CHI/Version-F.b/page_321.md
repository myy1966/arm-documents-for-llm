- Send Comp\_I if the cache line is not cached, or it is not known if the cache line is cached, in the cache at the next level.
- Send a Comp\_I response if either the cache look up at Home is a miss or Home did not look up the cache before responding.
- Permitted to use DMT to get data from SN-F to the Stash target in response to a Data Pull request.
- Permitted to use separate Non-data and Data-only response to the Stash target in response to a Data Pull request.

Stash target responsibilities:

- The snoop must not change the state of the cache line at the Stash target.
- The snoop is treated as a hint at the Stash target to obtain a copy of the cache line.
- Must not request DataPull if:

    - Snoop has an address hazard with an outstanding request.
    - Response is sent before performing a local cache lookup.
    - The snoop is SnpStashShared and the cache has a copy of the cache line.
    - The Stash target has an outstanding request to the same address that has received a DBIDRespOrd but not yet completed.

- When requesting DataPull:

    - The Stash target must guarantee the Read data is accepted without any structural or protocol dependencies that could result in deadlock.
    - The DataPull request is treated by Home as ReadNotSharedDirty for SnpOnceShared.
    - The DataPull request is treated by Home as ReadUnique for SnpOnceUnique.
    - The Home must treat the Stash request and the DataPull request atomically as a single request. That is, the Home must not order any other request to the same address between the Stash request and the corresponding DataPull request.
    - The Stash target must populate the DBID field in the response with the TxnID that is to be used by Home for the Read transaction.

- A DataPull request can be sent, but is not required to be sent, when the snoop is SnpStashUnique and a shared copy is present.
- The Stash target is permitted, but not required, to wait until the local cache lookup is complete before sending the Snoop response.
- The cache state in the Snoop response is not required to be precise:

    - An imprecise response must be SnpResp\_I.
    - Any state other than I in the response must be precise.

> **_NOTE:_** For StashOnce*, care is needed to avoid any action that could result in the deallocation of the cache line from the cache where it is expected to be used.
>
> A StashOnce*Unique transaction can cause the invalidation of a copy of the cache line and care must be taken to ensure such transactions do not interfere with Exclusive access sequences.

The requirements regarding the sending of Stash type snoops from a Home, and the permitted responses by the target, are the same as the request/response rules for StashOnceSep transactions. See B2.3.4 Stash transactions.