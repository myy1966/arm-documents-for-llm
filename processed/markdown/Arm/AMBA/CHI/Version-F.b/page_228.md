Table B4.32 Continued from previous page

| Response              | DAT Opcode | Resp[2:0] | Cache line state | Notes                                                                       |
|-----------------------|------------|-----------|------------------|-----------------------------------------------------------------------------|
| SnpRespData\_SC\_PD   | 0x1        | 0b101     | SC               | Responsibility for updating the memory is passed to the Home                |
| SnpRespDataPtl\_I\_PD | 0x5        | 0b100     | I                | Partial data. Responsibility for updating the memory is passed to the Home. |
| SnpRespDataPtl\_UD    | 0x5        | 0b010     | UDP              | Partial data                                                                |

Table B4.33 shows the permitted Forward type snoop responses with data, the DAT Opcode, Resp, and FwdState field encodings, and the meaning of the response.

Table B4.33: Permitted Forward type snoop responses with data

| Response                       | RSP Opcode | Resp[2:0] | FwdState[2:0] | Cache line state | Forwarded state | Notes                                                             |
|--------------------------------|------------|-----------|---------------|------------------|-----------------|-------------------------------------------------------------------|
| SnpRespData\_I\_Fwded\_SC      | 0x6        | 0b000     | 0b001         | I                | SC              |                                                                   |
| SnpRespData\_I\_Fwded\_SD\_PD  | 0x6        | 0b000     | 0b111         | I                | SD              | Responsibility for updating the memory is passed to the Requester |
| SnpRespData\_SC\_Fwded\_SC     | 0x6        | 0b001     | 0b001         | SC               | SC              |                                                                   |
| SnpRespData\_SC\_Fwded\_SD\_PD | 0x6        | 0b001     | 0b111         | SC               | SD              | Responsibility for updating the memory is passed to the Requester |
| SnpRespData\_SD\_Fwded\_SC     | 0x6        | 0b011     | 0b001         | SD               | SC              |                                                                   |
| SnpRespData\_I\_PD\_Fwded\_I   | 0x6        | 0b100     | 0b000         | I                | I               | Responsibility for updating the memory is passed to the Home      |
| SnpRespData\_I\_PD\_Fwded\_SC  | 0x6        | 0b100     | 0b001         | I                | SC              | Responsibility for updating the memory is passed to the Home      |
| SnpRespData\_SC\_PD\_Fwded\_I  | 0x6        | 0b101     | 0b000         | SC               | I               | Responsibility for updating the memory is passed to the Home      |
| SnpRespData\_SC\_PD\_Fwded\_SC | 0x6        | 0b101     | 0b001         | SC               | SC              | Responsibility for updating the memory is passed to the Home      |

The cache line state associated with a Snoop response with data must be a legal value, even if the RespErr field indicates there is a Data Error (DERR). A Snoop response with data is not permitted to have a NDERR. See B9.1.4.7 Snoop transactions.