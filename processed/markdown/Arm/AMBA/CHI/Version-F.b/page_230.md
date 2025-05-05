Table B4.34 Continued from previous page

| Response        | RSP Opcode | Resp[2:0] | Cache line state when response was sent | Action when a hidden copy of the cache line is at Home                                   | Notes                                            |
|-----------------|------------|-----------|-----------------------------------------|------------------------------------------------------------------------------------------|--------------------------------------------------|
| CompAck\_UC     | 0x2        | 0b010     | UC                                      | Expected, but not required, to be exposed, unless a Unique copy still exists elsewhere ᵃ |                                                  |
| CompAck\_SC     | 0x2        | 0b001     | SC                                      | Expected, but not required, to be exposed                                                |                                                  |
| CompAck\_UD\_PD | 0x2        | 0b110     | UD                                      | Expected, but not required, to be exposed, unless a Unique copy still exists elsewhere ᵃ | Responsibility for updating the memory is passed |
| CompAck\_SD\_PD | 0x2        | 0b111     | SD                                      | Expected, but not required, to be exposed                                                | Responsibility for updating the memory is passed |

- ᵃ A Unique copy can still exist at the Requester when the CopyBack Write transaction was a WriteClean.

**RetryAck**

- Sent by a Completer to a Requester if the request is not accepted at the Completer due to lack of appropriate resources.
- Response is permitted for any request transaction except PCrdReturn or PrefetchTgt.
- The RespErr field is applicable and must be set to 0.
- The Resp field is inapplicable and must be set to 0.

See B2.3.8 Retry.

**PCrdGrant**

- Grants a Protocol Credit. A subsequent request, sent using the Protocol Credit, is guaranteed to be accepted by the target.
- The RespErr field is applicable and must be set to 0.
- The Resp field is inapplicable and must be set to 0. See B2.3.8 Retry.

**ReadReceipt**

- Sent for a request that has an ordering requirement with respect to other ordered requests from the same Requester.
- Sent by a Subordinate Node to indicate it has accepted a Read request and will not send a RetryAck response.