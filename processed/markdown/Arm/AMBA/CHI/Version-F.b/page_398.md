- If a Requester cannot guarantee to write a full cache line irrespective of the Tag Match result, it is permitted to use either:

    - ReadClean with Transfer
    - ReadUnique with Transfer

See Table B4.37 for Requester cache state transitions.

When responding to a ReadClean, a Home that uses a Snoop Filter to track the cached state at the Requester, must not downgrade the state of the cache line in the Snoop Filter based on the state in the response to the Requester. That is, the Snoop filter must not change a line previously tracked as:

- Valid, to being tracked as Invalid.
- Unique, to being tracked as Shared.
- Dirty, to being tracked as Clean.

> **_NOTE:_** Prior to Issue F, I and UCE were the only permitted initial cache line states for the ReadClean transaction. The Home that uses a Snoop Filter to track the cached states was permitted to set the state of the cached line based on the state in the response.

#### B12.4.1.3 Permitted responses and tag state

The data and state of the cache line received with the Allocation Tags must be appropriately handled to not break coherency.

When the request TagOp value is Transfer, the permitted response field values are:

- Transfer. Indicates the returned tags are Clean.
- Update. Indicates the returned tags are Dirty. Data response must pass Dirty [\_PD].

When the request TagOp value is Fetch, the permitted response field values are:

- Transfer. Indicates the returned tags are Clean.
- Update. Indicates the returned tags are Dirty. Data response must pass Dirty [\_PD].

When the request TagOp value is Invalid, the permitted response field values are:

- Invalid. Indicates the returned tags are Invalid.
- Transfer. Indicates the returned tags are Clean.

When the TagOp value in Read data is invalid, TU must be all zeros. Tag is inapplicable and can take any value.

When data and response are separately sent in a Read transaction, the TagOp field is only applicable in the Data-only message. TagOp is inapplicable in the Non-data response message and must be set to 0.

The cache state that the tags must be held in is consistent with the type of the Read request:

- For all Read requests with a TagOp value of Invalid, Invalid or Clean tags must be returned.
- For ReadNoSnp with a TagOp value of Transfer or Fetch, Clean tags must be returned.
- For ReadClean, ReadOnce, ReadOnceCleanInvalid, and ReadOnceMakeInvalid with a TagOp value of Transfer, Clean tags must be returned.
- For ReadNotSharedDirty with a TagOp value of Transfer, Clean or Dirty tags must be returned. Dirty tags are permitted to be returned only if the cache line state is Unique.
- For ReadShared with a TagOp value of Transfer, Clean or Dirty tags must be returned.