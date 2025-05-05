In responses to stash snoops, the Snoopee can send a Read request combined with the Snoop response (SnpResp\_X\_Read), by setting the DataPull bit. The permitted Snoop responses with Data Pull are:

- For SnpUniqueStash:

    - SnpResp\_I\_Read
    - SnpRespData\_I\_Read
    - SnpRespData\_I\_PD\_Read
    - SnpRespDataPtl\_I\_PD\_Read

- For SnpMakeInvalidStash:

    - SnpResp\_I\_Read

- For SnpStashUnique:

    - SnpResp\_I\_Read
    - SnpResp\_UC\_Read
    - SnpResp\_SC\_Read
    - SnpResp\_SD\_Read

- For SnpStashShared:

    - SnpResp\_I\_Read
    - SnpResp\_UC\_Read

### B4.5.4 Miscellaneous response

This section describes responses that cannot be classified as a completion, WriteData, or Snoop response.

The miscellaneous responses are:

**CompAck**

- Sent by the Requester on receipt of the completion response.
- Used by Read, Dataless, WriteNoSnp, WriteUnique, and CopyBack Write transactions.
- The RespErr field is applicable and must be set to 0.
- For Immediate Write transactions, the Resp value in a CompAck response is inapplicable and must be set to 0.
- For CopyBack Write transactions, the Resp value in a CompAck response is applicable. The permitted values for Resp in CompAck are shown in Table B4.34.

Table B4.34: Permitted CompAck responses for CopyBack Write transactions

| Response   | RSP Opcode | Resp[2:0] | Cache line state when response | Action when a hidden copy of the | Notes                                          |
|------------|------------|-----------|--------------------------------|----------------------------------|------------------------------------------------|
| CompAck\_I | 0x2        | 0b000     | Imprecise and must be ignored  | Must not yet be exposed          | Indicates a CopyBack request has been canceled |

Continued on next page