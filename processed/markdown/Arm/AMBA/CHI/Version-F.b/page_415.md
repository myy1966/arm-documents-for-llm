RSP channel message:

- For a Comp response, the TagOp field is only used in response to a MakeReadUnique transaction and is used to indicate if responsibility for Dirty tags is being passed to the Requester or not.
- For all other RSP channel messages, the TagOp field is inapplicable and must be 0.

SNP message:

- The TagOp field is not present in the SNP channel.