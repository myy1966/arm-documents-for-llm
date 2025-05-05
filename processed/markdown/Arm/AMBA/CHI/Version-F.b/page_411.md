When the RespErr field in a response is NDERR:

- The TagOp in the response to the Requester is inapplicable and can take any value.
- The Snoop response must be Invalid.

Poison on tags is not supported. See B9.2.1 Poison.

### B12.11.3 MTE not supported

When a Completer does not support MTE for the address in the request, the Completer must send a TagOp value of Invalid in response to a Read transaction with a TagOp value of Transfer or Fetch. The returned tags must be set to 0. The returned tags can be cached as Clean by the Requester.

A Completer in response to a Read request to a Non-cacheable or Device memory location must set the TagOp value in the response to Invalid. A Completer is expected to give an OK response to an MTE operation, unless a different response can be given to an equivalent non-MTE operation.

When a Write request with TagOp Match is received and a Completer does not support MTE for the address in the request, the Completer is still required to send a TagMatch response. The Resp field value must indicate that the Tag Match failed. The Completer is permitted, but not required, to wait for the write data before sending the TagMatch response.