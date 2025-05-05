Table B8.5 Continued from previous page

| Field | Bits | Function                                                                                                                                                                                                                                                                                                                                          |
|-------|------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IS ᶜ  | 4    | Invalidation Size (IS) encoding for GPT TLBI by PA operations: </br> 0b0000        4K </br> 0b0001        16K </br> 0b0010        64K </br> 0b0011        2MB </br> 0b0100        32MB </br> 0b0101        512MB </br> 0b0110        1GB </br> 0b0111        16GB </br> 0b1000        64GB </br> 0b1001        512GB </br> 0b1010-0b1111 Reserved |

- ᵃ DVMv8 only.
- ᵇ Inapplicable and must be set to 0 in non-TLBI DVM operations. See B8.4.3.1 TLB Invalidate by Range and B8.4.3.2 Level Hint in TLBI operations for details of how these fields are used in TLBI operations.
- ᶜ Inapplicable and must be set to 0 in non-GPT TLBI by PA DVM operations. See B8.4.3.3 Invalidation Size in GPT TLBI by PA operations

***TTL* and *TG* fields**

For TLB Invalidations by address range, the TTL field can indicate which level of translation table walk holds the leaf entry for the address being invalidated. The encodings are shown in Table B8.6.

Table B8.6: Leaf entry hint for range-based TLB Invalidations

| TTL  | Meaning                                                     |
|------|-------------------------------------------------------------|
| 0b00 | No level hint information.                                  |
| 0b01 | The leaf entry is on level 1 of the translation table walk. |
| 0b10 | The leaf entry is on level 2 of the translation table walk. |
| 0b11 | The leaf entry is on level 3 of the translation table walk. |

For TLB Invalidations by non-range address, the TTL and TG fields indicate which level of translation table walk holds the leaf entry for the address being invalidated.

The encodings are shown in Table B8.7.