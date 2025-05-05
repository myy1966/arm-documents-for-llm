## B12.4 Read transaction rules

A read can optionally fetch tags along with the data. The need to return tags along with read data is determined from the value of TagOp in the request.

### B12.4.1 TagOp values

When TagOp value in the request is Transfer:

- Tags are required to be returned along with the data.
- The state of the returned tags must be the appropriate permitted cache state for the request being used.
- The number of tags to be returned is determined by the size of Data that is returned. For all Snoopable requests four tags per access must be returned.
- When required by the access, matching of Physical Tags against the Allocation Tags that are received along with read data is done at the Requester.

When TagOp value in the Request is Fetch:

- Tags are required to be returned along with data.
- Returned data is not required to be valid. The Requester must ignore the received data irrespective of the tag match result.
- All tags corresponding to a cache line must be returned.
- The state of the returned tags must be Clean or Dirty.
- If Dirty tags are returned, they must be preserved, unless updated, and written back to memory.

When TagOp value in the request is Invalid:

- It is permitted, but not required, that tags are returned along with the data.
- If tags are returned along with the data, they must be Clean.

#### B12.4.1.1 Converting tags from Shared to Unique

To update either the data or the tags or both, when both the data and the tags are present at the Requester in Shared state, and the Requester requires to move the cache line to a Unique state, the MakeReadUnique transaction with a TagOp value of Transfer is expected to be used. The Requester is permitted to use ReadUnique with a TagOp value of Transfer.

#### B12.4.1.2 Fetching tags when Data is present

If a Requester has a cached copy of a cache line, with data Valid but Allocation tags are not Valid, and the Requester requires a Tag Match to be performed, the Requester must use a Read request to fetch the required tags.

In the above scenario:

- If a Requester can guarantee to write a full cache line irrespective of the Tag Match result, it it permitted to use either:

    - ReadNoSnp with Fetch if the target memory location is Non-snoopable. The returned data is not required to be valid and must be dropped. Clean tags must be returned. All tags within the cache line must be Valid.
    - ReadUnique with Fetch, if the target memory location is Snoopable. The returned data is not required to be valid and must be dropped. Clean or Dirty tags must be returned. All tags within the cache line must be Valid.