Table B8.12 Continued from previous page

| Operation                                       | Arm  | Exception | Security | VMIDV | ASIDV | Leaf | Stage | AddrV |
|-------------------------------------------------|------|-----------|----------|-------|-------|------|-------|-------|
| Realm Guest OS TLBI by ASID and VA, Leaf only   | v9.2 | 0b10      | 0b00     | 0b1   | 0b1   | 0b1  | 0b00  | 0b1   |
| Realm Guest OS TLBI by IPA                      | v9.2 | 0b10      | 0b00     | 0b1   | 0b0   | 0b0  | 0b10  | 0b1   |
| Realm Guest OS TLBI by IPA, Leaf only           | v9.2 | 0b10      | 0b00     | 0b1   | 0b0   | 0b1  | 0b10  | 0b1   |
| Realm Hypervisor TLBI all                       | v9.2 | 0b11      | 0b00     | 0b0   | 0b0   | 0b0  | 0b00  | 0b0   |
| Realm Hypervisor TLBI by VA                     | v9.2 | 0b11      | 0b00     | 0b0   | 0b0   | 0b0  | 0b00  | 0b1   |
| Realm Hypervisor TLBI by VA, Leaf only          | v9.2 | 0b11      | 0b00     | 0b0   | 0b0   | 0b1  | 0b00  | 0b1   |
| Realm Hypervisor TLBI by ASID                   | v9.2 | 0b11      | 0b00     | 0b0   | 0b1   | 0b0  | 0b00  | 0b0   |
| Realm Hypervisor TLBI by ASID and VA            | v9.2 | 0b11      | 0b00     | 0b0   | 0b1   | 0b0  | 0b00  | 0b1   |
| Realm Hypervisor TLBI by ASID and VA, Leaf only | v9.2 | 0b11      | 0b00     | 0b0   | 0b1   | 0b1  | 0b00  | 0b1   |
| GPT TLBI by PA                                  | v9.2 | 0b01      | 0b10     | 0b0   | 0b0   | 0b0  | 0b11  | 0b1   |
| GPT TLBI by PA, Leaf only                       | v9.2 | 0b01      | 0b10     | 0b0   | 0b0   | 0b1  | 0b11  | 0b1   |
| GPT TLBI all                                    | v9.2 | 0b01      | 0b10     | 0b0   | 0b0   | 0b0  | 0b11  | 0b0   |

#### B8.4.3.1 TLB Invalidate by Range

When DVM\_Support is DVM\_v8.4 or greater, TLBI operations by IPA or VA have the option to operate on an address range if the Range field is 0b1.

Range-based TLBI operations include range-specific payload in addition to the payload fields in non-range based TLBI operation.

##### B8.4.3.1.1 Range-based payload packing for TLBI by VA and IPA operations

The range-based fields for TLBI operations by VA and IPA are:

- Range
- BaseAddr
- TG
- TTL
- Scale
- Num

> **_NOTE:_** The TG and TTL fields can be used as Level hints for Non-range based TLBI operations by VA or IPA. See B8.4.3.2 Level Hint in TLBI operations.

When the Range field is set to 1 for TLBI operations by V A or IPA, the address range to invalidate is calculated using the following formula, where Translation\_Granule\_Size in bytes is determined from the TG value, as shown in Table B8.13:

$$
BaseAddr \leq AddressRange \lt BaseAddr + ((Num + 1) × 2^{(5 \times Scale+1)} × Translation_Granule_Size)
$$