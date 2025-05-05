## B12.13 TagOp field use summary

The following sections give a summary of the use of the TagOp field in messages in different channels:

REQ channel message:

- Read* and MakeReadUnique transaction:

    - TagOp field can be Invalid, Transfer, or Fetch.
    - TagOp Fetch is permitted only in ReadUnique, ReadNoSnp, and ReadNoSnpSep transactions.
    - TagOp field Transfer indicates whether Allocation Tags must be returned alongside read data.
    - TagOp field Fetch indicates only valid tags are required to be returned. Returned data is not required to be valid.
    - For all other REQ channel messages, the TagOp field is inapplicable and must be 0.
    - The TagOp field Match cannot be used in an Exclusive transaction.

- Write transaction:

    - TagOp field can be Invalid, Transfer, Match or Update.
    - TagOp field Transfer indicates Clean tags are being transferred and tags can be cached alongside the data.
    - TagOp field Match indicates a Match check is required between the Physical Tags in the message and the Allocation Tags at the memory location.
    - TagOp field Update indicates Dirty tags are being passed, which must update the Allocation Tag values.

- MakeUnique transaction:

    - TagOp field can be Invalid or Update.
    - TagOp field Update indicates all tags are written to.

- Atomic transaction:

    - TagOp field can be Invalid or Match.
    - TagOp field Match indicates whether a Tag Match is required.

- StashOnce transaction:

    - TagOp field can be: Invalid or Transfer.
    - TagOp field Transfer indicates whether Allocation Tags should be stashed alongside Stash data.

- PrefetchTgt transaction:

    - TagOp value can be Invalid or Transfer.
    - For all the other REQ channel messages, the TagOp field is inapplicable and must be 0.

DAT channel message:

- For Read data, the TagOp field indicates whether the Allocation Tags sent along with the data are Invalid, Clean, or Dirty.
- For Snoop data, the TagOp field indicates whether the Allocation Tags sent in the Snoop response are Invalid, Clean, or Dirty.
- For write data, the TagOp field indicates whether the Allocation Tags sent in the write data are Invalid, Clean, Dirty, or a Match check is required. The TagOp value must be the same as in the Request message except when a snoop has downgraded the state of the tags or the write has been canceled.