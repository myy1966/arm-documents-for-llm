Table B4.31 Continued from previous page

| Response                                    | RSP Opcode | Resp[2:0] | FwdState[2:0] | Cache line state at Snoopee | Forwarded state | Notes                                                                                                          |
|---------------------------------------------|------------|-----------|---------------|-----------------------------|-----------------|----------------------------------------------------------------------------------------------------------------|
| SnpResp\_SC\_Fwded\_SD\_PD                  | 0x9        | 0b001     | 0b111         | SC                          | SD              | Responsibility for updating the memory is passed                                                               |
| SnpResp\_UC\_Fwded\_I SnpResp\_UD\_Fwded\_I | 0x9        | 0b010     | 0b000         | UC or UD                    | I               | Note A single encoding is used to indicate that the cache line is Unique. This encoding is used for UC and UD. |
| SnpResp\_SD\_Fwded\_I                       | 0x9        | 0b011     | 0b000         | SD                          | I               |                                                                                                                |
| SnpResp\_SD\_Fwded\_SC                      | 0x9        | 0b011     | 0b001         | SD                          | SC              |                                                                                                                |

Table B4.32 shows the permitted Non-forward type snoop responses with data, the DAT Opcode and Resp field encodings, and the meanings of the response.

Table B4.32: Permitted Non-forward type snoop responses with data

| Response                        | DAT Opcode | Resp[2:0] | Cache line state | Notes                                                                                                          |
|---------------------------------|------------|-----------|------------------|----------------------------------------------------------------------------------------------------------------|
| SnpRespData\_I                  | 0x1        | 0b000     | I                |                                                                                                                |
| SnpRespData\_UC SnpRespData\_UD | 0x1        | 0b010     | UC or UD         | Note A single encoding is used to indicate that the cache line is Unique. This encoding is used for UC and UD. |
| SnpRespData\_SC                 | 0x1        | 0b001     | SC               |                                                                                                                |
| SnpRespData\_SD                 | 0x1        | 0b011     | SD               |                                                                                                                |
| SnpRespData\_I\_PD              | 0x1        | 0b100     | I                | Responsibility for updating the memory is passed to the Home                                                   |
| SnpRespData\_UC\_PD             | 0x1        | 0b110     | UC               | Responsibility for updating the memory is passed to the Home                                                   |

Continued on next page