## B12.10 Home to Subordinate transactions

For a Read request to the Subordinate:

- The permitted TagOp values are Invalid, Transfer, and Fetch.

For a Write request to the Subordinate:

- The permitted TagOp values are Invalid, Transfer, Update, and Match.

For an Atomic request to the Subordinate:

- The permitted TagOp values are Invalid, and Match.

A ReadNoSnp or ReadNoSnpSep with TagOp Transfer or Fetch can be used to fetch tags from the Subordinate. Tags can be returned from a Subordinate to the Home directly or sent to the Requester using DMT. When TagOp Fetch is used, the Subordinate is not required to return valid data. TagOp Fetch is permitted only with a data size of 64 bytes.

When memory needs to be updated with tags, WriteNoSnp with TagOp Update must be used. When only tags need to be updated the data BE bits can be set to all 0.

When TagOp is Match, the TagGroupID in WriteNoSnp and Atomic transactions to the Subordinate are applicable, and these values must be returned in the TagMatch response.

When Atomic operations are performed at the Subordinate Node, the Home is permitted to include TagOp Match in Atomic requests to the Subordinate. Where the tag match is performed at the Subordinate, in both non-Store Atomic and Store Atomic transactions, the TagMatch response TgtID must be obtained from the ReturnNID value in the request. To support this feature, it is required that the ReturnNID in the Atomic Store from a Home Node to a Subordinate Node is applicable and must be set to the same value as the SrcID in the request.

> **_NOTE:_** Applicability of the ReturnNID in non-Store Atomic transactions is already a requirement in the previous version of this specification.