Table B7.1 Continued from previous page

| Stash request      | Snoop request  |
|--------------------|----------------|
| StashOnceShared    | SnpStashShared |
| StashOnceSepShared | SnpStashShared |

- ᵃ Possible if Home already has the latest copy of the line.

A Snoopee that receives a Stash Snoop request does one of the following:

- Provides a Snoop response that also acts as a Read request for the associated cache line. Including a Read request with Snoop response is referred to as a DataPull. Table B7.2 shows the type of Read request that is implied by a DataPull in the response to each Stash Snoop request.
- Provides a Snoop response without a DataPull response so ignoring the cache stash hint.

Table B7.2: Snoop response with Data Pull and implied Read request

| Snoop request       | Implied Read request |
|---------------------|----------------------|
| SnpUniqueStash      | ReadUnique           |
| SnpMakeInvalidStash | ReadUnique           |
| SnpStashUnique      | ReadUnique           |
| SnpStashShared      | ReadNotSharedDirty   |

The value of the DataPull field in the SnpResp and SnpRespData responses indicates if DataPull is requested. See B13.10.37 Data Pull, DataPull for legal values for DataPull.

The use of DataPull to complete a Snoop request with Stash is optional.

If the Snoopee is not able to support the DataPull transaction flow, the stash operation is permitted to be ignored.