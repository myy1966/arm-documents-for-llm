## B12.5 Write transactions

Different fields to support MTE are distributed between the Request and Data message of a Write transaction. The TagOp field, which indicates the operation to be performed on the tags in the WriteData message, is included in both the Request and WriteData message. The Request also includes the TagGroupID field to provide an identifier for the pass/fail response for a request that requires a Tag Match operation. When the TagOp field in the Request is Match, the Excl field must be 0.

> **_NOTE:_** The use of the TagGroupID field is IMPLEMENTATION DEFINED. Typically, TagGroupID can be used to identify the Exception level and TTBR which a response relates to.

The TagOp value in the WriteData message is typically the same as the value in the Request message, except when either the write data is snooped out or the write is canceled. Whether or not to perform a Tag Match must be decided based on the TagOp value in the WriteData, when the TagOp values in the WriteData and Write request are different.

The WriteData message also includes a Tag Update (TU) bit per tag, which is applicable when TagOp is Update.

### B12.5.1 Permitted TagOp values

This section describes the permitted WriteData TagOp values for each of the permitted TagOp values in the Write request message.

When the TagOp field in the Request is Invalid, the Memory Tagging fields in the WriteData must be set to 0 and ignored by the Completer.

When the TagOp field in the Request is Transfer, the TagOp field in the WriteData can be:

- Transfer: The Tags are Clean and must be handled appropriately by the Completer.
- Invalid: This is possible only if either the cached copy is invalidated, or the Write transaction is canceled.

In a WriteClean transaction where the Request TagOp is Transfer, the TagOp in the Write data is not permitted to be changed to Update.

When the TagOp field in the request is Update, the TagOp field in the WriteData can be:

- Update: The Dirty tags must be cached or written to memory.
- Transfer: The Tags are Clean. This is possible if the Dirty tags have been snooped out.
- Invalid: This is possible only if either the cached copy is invalidated or the Write transaction is canceled.

When the TagOp field in the request is Match the TagOp field in the WriteData can be:

- Match: The appropriate Tag Match must be performed at the Completer.
- Invalid: This is possible only if the Write transaction is canceled.

### B12.5.2 TagOp, TU, and tags relationship

This section describes the relationship between TagOp, TU, and tags in different Write transactions:

- For all Write requests with TagOp Invalid, the Memory Tagging fields must be set to 0 and ignored by the Completer.
- For WriteBackFull and WriteCleanFull with TagOp: