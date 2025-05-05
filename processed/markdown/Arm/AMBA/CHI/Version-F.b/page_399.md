- For ReadUnique with a TagOp value of Transfer or Fetch, Clean or Dirty tags must be returned. The returned cache line state must be Unique.
- For MakeReadUnique with a TagOp value of Invalid, Invalid or Clean tags must be returned. Clean tags are only permitted in responses with data.
- For MakeReadUnique with a TagOp value of Transfer, if data is included in the response, Clean or Dirty tags must be returned.

    - Clean tags are permitted in responses with data.
    - Dirty tags are only permitted when the response is transferring the responsibility of updating Dirty data, that is, the response includes [UD\_PD].
    - Dataless responses using Comp\_UC or Comp\_SC are permitted to signal Clean tags are being transferred, despite no Tag transfer occuring.

- In the case where Dirty tags are returned, the cache line returned must include pass Dirty [\_PD].

When MTE is not supported for the targeted address, the response must use TagOp of Invalid.

For an Exclusive access sequence, the fetching of tags must avoid any form of request that Invalidates other copies of the cache line before the Exclusive Store transaction is performed. Typically, this is achieved by fetching tags at the same time the Exclusive Load transaction is performed.

### B12.4.2 Permitted initial MTE tag states

Table B12.2 shows the permitted initial data state along with tag state for different Read transactions and permitted TagOp value in the corresponding request. The combination of tag and data states must obey the coherency rules described in B12.3 Tag coherency.

Table B12.2: Permitted initial Tag states and request TagOp values in Read transactions

| Request                                                      | TagOp                    | Data state | Tag state             |
|--------------------------------------------------------------|--------------------------|------------|-----------------------|
| ReadNoSnp                                                    | Invalid, Transfer, Fetch | I          | Invalid               |
| ReadOnce </br> ReadOnceMakeInvalid </br> ReadOnceMakeInvalid | Invalid, Transfer        | I          | Invalid               |
| ReadNotSharedDirty </br> ReadShared                          | Invalid, Transfer        | I, UCE     | Invalid               |
| ReadClean                                                    | Invalid                  | I, UCE     | Invalid               |
| ReadClean                                                    | Transfer                 | I,UCE,UDP  | Invalid               |
| ReadClean                                                    | Transfer                 | SC, UC     | Invalid, Clean        |
| ReadClean                                                    | Transfer                 | SD, UD     | Invalid, Clean, Dirty |
| ReadPreferUnique                                             | Invalid, Transfer        | I, UCE     | Invalid               |
| ReadPreferUnique                                             | Invalid, Transfer        | SC         | Invalid, Clean        |
| ReadPreferUnique                                             | Invalid, Transfer        | SD         | Invalid, Clean, Dirty |
| ReadUnique                                                   | Invalid, Transfer, Fetch | I, UCE     | Invalid               |
| ReadUnique                                                   | Invalid, Transfer, Fetch | SC, UC     | Invalid, Clean        |

Continued on next page