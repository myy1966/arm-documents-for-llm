- Permitted to return Dirty tags to the Home.
- Dirty tags must be kept at the Snoopee if the data transfer to Home is not performed.
- Dirty tags must be written back to Home if the cache line is being invalidated or Dirty data is being written back to Home.

A Snoopee is permitted, but not required, to convert any Forwarding snoop to its corresponding Non-forwarding snoop.

> **_NOTE:_** This property is similar to that in the Non-MTE case.

See B12.9.4 Permitted TagOp values in Snoop responses for more details.

### B12.9.3 Stash snoops

Because the SNP channel does not include a TagOp field, the Home cannot forward the TagOp intentions of the Requester to the Stash target.

The permitted TagOp values in Snoop responses are:

- Invalid in response to SnpStash*.
- Invalid, Transfer, and Update in response to SnpUniqueStash.
- Invalid in response to SnpMakeInvalidStash.

See B12.9.4 Permitted TagOp values in Snoop responses for more details.

The requirements for determining the TagOp value in the Read request implied from the Data Pull request in the Snoop response are as follows:

For a DataPull request in response to SnpStash*:

- If the TagOp value in the original request is Transfer, it is recommended that Clean tags are returned in response to the Data Pull request.
- If the TagOp value in the original request is Invalid, it is recommended that Clean tags are returned in response to the Data Pull request if tags are available.

For a DataPull request in response to SnpUniqueStash:

- If tags are available when data is returned, irrespective of the presence or absence of data in the Snoop response and for any cache state, it is recommended that the Clean tags are returned in response to a Data Pull request.

### B12.9.4 Permitted TagOp values in Snoop responses

The permitted tag field values in Snoop responses are:

- For SnpResp, the TagOp field is inapplicable and must be set to 0.
- For SnpRespDataPtl, the permitted TagOp value is Invalid. Both the TU and the Tag field must be set to 0 and ignored by the receiver.
- For SnpRespData:

    - Invalid. All Tag fields must be set to 0.
    - Transfer. Clean tags must be returned. TU bits are inapplicable and must be set to 0.