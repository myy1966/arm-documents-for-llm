### B13.10.42 Tag Update, TU

TU[n-1:0]. This field indicates which of the Allocation Tags must be updated. There is one TU bit for each tag. Only valid in Snoop responses and Write transactions which update the Allocation Tags. Must be set to 0 in all other transactions.

TU[n-1] corresponds to [Tag[(4*n)-1 : 4*(n-1)]

### B13.10.43 Tag Group Identifier, TagGroupID

This field is used by a Requester to process different sets of TagMatch responses by grouping the corresponding requests together and identifying each group using TagGroupID. The precise contents of TagGroupID are IMPLEMENTATION DEFINED. Typically, TagGroupID is expected to contain an Exception Level, TTBR value, and CPU identifier.

TagGroupID is applicable in requests where TagOp is set to Match and in a TagMatch response.

In requests, when applicable, the same bits in the packet are used for LPID, PGroupID, or StashGroupID.

In responses, when applicable, the same bits in the packet are used for DBID, PGroupID, or StashGroupID.

### B13.10.44 Trace Tag, TraceTag

This field is a bit in a packet used to tag the packets associated with a transaction for tracing purposes.

Table B13.32 shows the TraceTag field value encodings.

Table B13.32: TraceTag value encodings

| TraceTag | Description          |
|----------|----------------------|
| 0        | Packet is not tagged |
| 1        | Packet is tagged     |

See Chapter B11 System Control, Debug, Trace, and Monitoring.

### B13.10.45 Memory System Resource Partitioning and Monitoring, MPAM

This field is used to efficiently utilize the memory resources among users and to monitor their use. See B11.4 MPAM.

### B13.10.46 Virtual Machine Identifier Extension, VMIDExt

This field is used to extend VMID value from 8 bits to 16 bits. See B8.4.1 DVM message payload.

### B13.10.47 Response Error, RespErr

This field indicates the error status of the response. See Chapter B9 Error Handling.

Table B13.33 shows the RespErr value encodings.