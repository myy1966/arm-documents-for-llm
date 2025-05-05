## B12.6 Dataless transactions

MakeUnique is the only Dataless transaction that supports the use of the TagOp field. In all other Dataless transactions, the TagOp field is inapplicable and must be set to all zeros.

The TagOp value in MakeUnique request can be Invalid or Update only. A Request TagOp value of Update is an indication that the Requester updates the tags along with data. Home, in response to MakeUnique, is permitted to use SnpMakeInvalid only when either the Request TagOp value is Update or the Home knows that the Snoopee does not have Dirty tags.

The only permitted TagOp value in response to MakeUnique is Invalid.

Cache Maintenance Operations must operate on both the data and the corresponding memory tags. A MakeInvalid that permits dropping of Dirty data without writing to memory must write Dirty tags to memory.