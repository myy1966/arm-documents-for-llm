**CopyBackWriteData, CBWrData**

Used for WriteBack, WriteClean, WriteEvictFull, and WriteEvictOrEvict, and CopyBack Combined Write transactions. Transfers coherent data from the cache at the Requester to the interconnect. Includes an indication of the cache line state prior to sending the WriteData response.

**NonCopyBackWriteData, NCBWrData**

Used for WriteUnique and WriteNoSnp, WriteNoSnpDef, and Combined Immediate Write transactions. Also used for a DVMOp transaction. The cache state in the response must be I.

**NonCopyBackWriteDataCompAck, NCBWrDataCompAck**

Used for Immediate Write and Combined Write transactions. Combined NonCopyBackWriteData and CompAck. The cache state in the response must be I.

**WriteDataCancel**

Used to inform the Completer that a Write request is canceled before write data is sent.

-  A Request Node can send WriteDataCancel instead of NonCopyBackWriteData in WriteNoSnpPtl, WriteUniquePtl, WriteUniquePtlStash, and corresponding Combined Write transactions.
-  A Home Node can send WriteDataCancel instead of NonCopyBackWriteData in WriteNoSnpFull, WriteNoSnpPtl, and corresponding Combined Write transactions to the Subordinate Node.
-  A Request Node or Home Node can send WriteDataCancel instead of NonCopyBackWriteData in WriteNoSnpDef transactions, if NDERR, OK/Defer, or OK/Unsupported are seen in a:

    - Comp response that arrives before NonCopyBackWriteData is sent
    - CompDBIDResp response

-  Must not be used in Write requests to Device memory, except during WriteNoSnpDef transactions.
- All data packets originally intended to be transferred must be sent. BE field value in the WriteDataCancel message must be set to all zeroes.
- Cache state in the response must be I.

The response includes the Resp field, which indicates the following:

**Cache state** Indicates the state of the cache line before sending the WriteData response. This state can differ from the state of the cache line when the original transaction request was sent if a snoop request, to the same address, is received by the Requester after sending the original transaction request, but before sending the corresponding WriteData response.

**Pass Dirty** Indicates if the responsibility for updating memory is passed by the Requester. The assertion of the Pass Dirty bit is shown by \_PD in the response name.

Table B4.29 shows the permitted WriteData responses, the Opcode and Resp field encodings, and the meaning of the response.

Table B4.29: Permitted WriteData responses, and Opcode and Resp field encodings

| Response             | DAT Opcode | Resp[2:0] | Cache line                     | Notes                                                                                                             |
|----------------------|------------|-----------|--------------------------------|-------------------------------------------------------------------------------------------------------------------|
| CopyBackWriteData\_I | 0x2        | 0b000     | Imprecise and must be ignored. | Indicates a CopyBack request has been canceled. The data in the response must be 0 and all BE must be deasserted. |

Continued on next page