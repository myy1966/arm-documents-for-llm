Table B4.25 Continued from previous page

| Request category | Request     | Expected Snoop |
|------------------|-------------|----------------|
| Others           | DVMOp       | SnpDVMOp       |
| Others           | PCrdReturn  | n/a            |
| Others           | PrefetchTgt | n/a            |

- ᵃ Forwarding snoops cannot be used for requests of less than 64B.
- ᵇ Home is expected to use SnpUniqueFwd if the Requester is determined to have lost its copy of the cache line.
- ᶜ Possible if Home already has the latest copy of the line.

The interconnect has the following behavior when generating a snoop request on receipt of a request from a Request Node:

- This specification supports a snoop filter or directory within the interconnect to track the state of cache lines present in RN-F caches. The tracking can be as detailed as knowing each RN-F that has a copy of the cache line, or as nonspecific as knowing that a cache line is present in one of the RN-F caches. Such tracking permits the interconnect to filter unnecessary snooping of an RN-F, for example:

    - If the snoop filter indicates that the cache line is not present in any of the RN-F caches, the interconnect does not send a snoop request.
    - If the cache line in the RN-F caches is already in the required state, for example the received request is ReadShared and all cached copies of the cache line are in SC state, the interconnect does not send a snoop request.

- The interconnect in response to a WriteUniqueFull, WriteUniqueFullStash, MakeUnique, and MakeInvalid must not use the SnpMakeInvalid snoop request unless either:

    - The transaction TagOp value is Update.
    - The interconnect can determine that the Snoopee does not hold Dirty tags.

- The interconnect in response to a MakeReadUnique must not use the SnpMakeInvalid Snoop request unless the interconnect can determine either that:

    - The Requester still has a cached copy of the cache line and the Snoopee does not have Dirty tags.
    - The Requester has lost its cached copy and the Snoopee does not have a Dirty copy of the cache line.

- It is permitted for the interconnect to generate a snoop request spontaneously without a corresponding request from a Request Node. For example, the interconnect can send a SnpUnique or SnpCleanInvalid request as a result of a backward invalidation from a snoop filter or interconnect cache.
- It is permitted for the interconnect to select which snoop request to send. For example:

    - For a WriteUniquePtl request, either a SnpCleanInvalid or SnpUnique snoop request can be sent. Both of these snoop transactions invalidate the cache line. If the cache line is dirty, data is returned with the response. The write data is written to memory once all Snoop responses are received and the partial data has been merged with any dirty data received with the Snoop response. The only difference in the behavior between the SnpCleanInvalid and SnpUnique snoop requests is that SnpUnique can return data from the UniqueClean (UC) state but SnpCleanInvalid does not. Using SnpUnique therefore could result in an unnecessary data transfer. This example shows the disadvantage of using SnpUnique instead of SnpCleanInvalid in certain circumstances.

- The interconnect is permitted to: