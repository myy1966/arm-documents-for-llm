> **_NOTE:_** The Snoop response cache state information provides the state of the cache line after the Snoop response is sent. This is different from:
>
> - A WriteData response, where the cache state information provides the state of the cache line at the point the write data is sent.
> - A read data response, where the cache state information indicates the permitted state of the cache line after the transaction completes.

Table B4.30 shows the permitted Non-forward type snoop responses without data, the RSP Opcode and Resp field encodings, and the meaning of the response.

Table B4.30: Permitted Non-forward type snoop responses without data

| Response    | RSP Opcode | Resp[2:0] | Cache line state  |
|-------------|------------|-----------|-------------------|
| SnpResp\_I  | 0x1        | 0b000     | I                 |
| SnpResp\_SC | 0x1        | 0b001     | SC or I           |
| SnpResp\_UC | 0x1        | 0b010     | UC, UCE, SC, or I |
| SnpResp\_UD | 0x1        | 0b010     | UD                |
| SnpResp\_SD | 0x1        | 0b011     | SD                |

Table B4.31 shows the permitted Forward type snoop responses without data, the RSP Opcode, Resp, and FwdState field encodings, and the meaning of the response. The permitted Forward type snoop responses listed in Table B4.31 forward a copy of the data to the Requester.

Table B4.31: Permitted Forward type snoop responses without data

| Response                  | RSP Opcode | Resp[2:0] | FwdState[2:0] | Cache line state at Snoopee | Forwarded state | Notes                                            |
|---------------------------|------------|-----------|---------------|-----------------------------|-----------------|--------------------------------------------------|
| SnpResp\_I\_Fwded\_I      | 0x9        | 0b000     | 0b000         | I                           | I               |                                                  |
| SnpResp\_I\_Fwded\_SC     | 0x9        | 0b000     | 0b001         | I                           | SC              |                                                  |
| SnpResp\_I\_Fwded\_UC     | 0x9        | 0b000     | 0b010         | I                           | UC              |                                                  |
| SnpResp\_I\_Fwded\_UD\_PD | 0x9        | 0b000     | 0b110         | I                           | UD              | Responsibility for updating the memory is passed |
| SnpResp\_I\_Fwded\_SD\_PD | 0x9        | 0b000     | 0b111         | I                           | SD              | Responsibility for updating the memory is passed |
| SnpResp\_SC\_Fwded\_I     | 0x9        | 0b001     | 0b000         | SC                          | I               |                                                  |
| SnpResp\_SC\_Fwded\_SC    | 0x9        | 0b001     | 0b001         | SC                          | SC              |                                                  |

Continued on next page