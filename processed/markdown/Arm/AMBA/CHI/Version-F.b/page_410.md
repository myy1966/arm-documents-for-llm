## B12.11 Error response

The following sub-sections describe Error response handling for:

- B12.11.1 Tag Match
- B12.11.2 Non-Tag Match errors
- B12.11.3 MTE not supported

### B12.11.1 Tag Match

Write and Atomic transactions that have TagOp value of Match in the Request must return the results of the Tag Match operation. The results are returned using the TagMatch message. The transaction must proceed as normal irrespective of the Tag Match result. The TagMatch response must be sent even if the WriteData is canceled or a Tag Match is not performed.

> **_NOTE:_** Using a separate TagMatch message adds complexity and extra messages to the Write and Atomic transactions. A separate TagMatch message also has the advantage to provide a sufficiently accurate response mechanism. Using a separate response does not delay the sending of the Comp response.

The TagMatch message characteristics are:

- The Home Node or Subordinate Node performing the Tag Match operation sends the TagMatch response.
- The TgtID value in the message is copied from:

    - SrcID in the request if the Completer is a Home Node.
    - ReturnNID in the request if the Completer is a Subordinate Node. The ReturnNID can point to the Requester or the Home. When the Subordinate returns the TagMatch response to the Home, if required by the transaction, the Home is responsible for forwarding the response to the Requester.

- The response must return the TagGroupID value from the request.
- The TraceTag field is inapplicable and can take any value.
- The Resp field value in the response indicates the Tag Match state as either pass or fail. See B13.10.48 Response status, Resp.
- The TagMatch response can be sent as soon as the Completer can determine the result. TagMatch is permitted to be sent without waiting for data. This can occur when the Completer does not support MTE.
- The Resp value in the TagMatch response must be:

    - A Fail when MTE is not supported.
    - A Pass when MTE is supported but the Tag Match is not performed. For example, when a write targets an MTE capable location, but fails an access permissions check.
    - Accurate, if the match is performed.

### B12.11.2 Non-Tag Match errors

Permitted Data and Non-data Error responses to requests are independent of the presence or absence of Memory Tagging.

Permitted RespErr field values in the TagMatch response are OK, DERR, and NDERR. See B9.1.4 Error response use by transaction type.