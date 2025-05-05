| Response                    | DAT Opcode | Resp[2:0] | Cache line state when data was sent | Notes                                                                                                                     |
|-----------------------------|------------|-----------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| CopyBackWriteData\_UC       | 0x2        | 0b010     | UC                                  | Data corresponding to a CopyBack request.                                                                                 |
| CopyBackWriteData\_SC       | 0x2        | 0b001     | SC                                  | Data corresponding to a CopyBack request.                                                                                 |
| CopyBackWriteData\_UD\_PD   | 0x2        | 0b110     | UD or UDP                           | Data corresponding to a CopyBack request. Responsibility for updating the memory is passed.                               |
| CopyBackWriteData\_SD\_PD   | 0x2        | 0b111     | SD                                  | Data corresponding to a CopyBack request. Responsibility for updating the memory is passed.                               |
| NonCopyBackWriteData        | 0x3        | 0b000     | I                                   | Data corresponding to an Immediate Write request.                                                                         |
| NonCopyBackWriteDataCompAck | 0xC        | 0b000     | I                                   | Data corresponding to an Immediate Write request and combined CompAck to indicate that the transaction has completed.     |
| WriteDataCancel             | 0x7        | 0b000     | I                                   | Indicates an Immediate Write request has been canceled. The data in the response must be 0 and all BE must be deasserted. |

> **_NOTE:_** The cache line state at the Requester after the Write transaction has completed is not determined from the cache state information in the WriteData response. The cache line can be determined to remain Valid or not after the transaction by the opcode of the transaction:
>
> - A WriteBack or WriteEvictFull transaction must be in I state.
> - A WriteClean transaction can remain allocated and be in a Clean state.

### B4.5.3 Snoop response

A Snoop transaction includes a Snoop response. A Snoop response can be with or without data. The forms of Snoop response are:

**Snoop response without data**

- This Snoop response is used when no data transfer is required.
- It is sent on the SRSP channel and uses the SnpResp opcode.
- For Stash snoops, a DataPull request can be included.
- Snoop response without data is always used for the response to a SnpDVMOp transaction.