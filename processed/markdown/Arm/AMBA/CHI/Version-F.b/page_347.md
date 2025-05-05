Table B8.13: TG field encodings in TLB instructions that apply to a range of addresses

| TG | Translation granule size | Translation\_Granule\_Size |
|----|--------------------------|----------------------------|
| 00 | Reserved                 | Not applicable             |
| 01 | 4KB translation granule  | 4096                       |
| 10 | 16KB translation granule | 16384                      |
| 11 | 64KB translation granule | 65536                      |

The range parameters are placed in the request packets as shown in Table B8.10.

The Range and Num values are carried on the FwdNID field in the Snoop flit alongside the Addr field for the corresponding Snoop transaction. Unused bits of FwdNID in SnpDVMOp must be set to 0.

Table B8.14 shows the placement of the Range and Num values in the SnpDVMOp payload.

Table B8.14: Num value placement in SnpDVMOp payload

| FwdNID bit | SnpDVMOp request | SnpDVMOp request |
|------------|------------------|------------------|
|            | Part 1           | Part 2           |
| 0          | Range            | Num[0]           |
| 1          | 0                | Num[1]           |
| 2          | 0                | Num[2]           |
| 3          | 0                | Num[3]           |
| 4          | 0                | Num[4]           |
| 5          | 0                | 0                |
| 6          | 0                | 0                |

#### B8.4.3.2 Level Hint in TLBI operations

Non-range based TLBI operations by VA or IPA operations are permitted to use TG and TTL fields. These operations use TG and TTL as an indication of the level of the page table walk that holds the leaf entry for the address that is being invalidated. For such operations, the following conditions apply:

- The Range field must be set to 0.
- The Num and Scale fields are inapplicable and must be set to 0.

#### B8.4.3.3 Invalidation Size in GPT TLBI by PA operations

GPT TLBI by PA operations perform range-based invalidation and invalidate TLB entries starting from the PA, within the range as specified in the IS field.

The range-based fields for GPT TLBI operations by PA are IS and PA. If the PA is not aligned to the IS value, no TLB entries are required to be invalidated.

The IS field is applicable only in GPT TLBI by PA operations.

The Range field is applicable and must be set to 1 for GPT TLBI by PA operations.

The Range field is applicable and must be set to 0 for GPT TLBI all operations.