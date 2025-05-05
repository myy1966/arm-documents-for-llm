#### B8.4.5.1 Physical Instruction Cache Invalidate

This section describes the Physical Instruction Cache Invalidate (PICI) operations that the DVM message supports. This message type is also used for Instruction Caches which are Virtually Indexed Physically Tagged (VIPT).

The fixed field values for a PICI message are shown in Table B8.17.

Table B8.17: Fixed field values for a Physical Instruction Cache Invalidate message

| Field     | Value | Status                                 |
|-----------|-------|----------------------------------------|
| DVMType   | 0b010 | Physical Instruction Cache Invalidate  |
| Part Num  | -     | See Table B8.10                        |
| Exception | 0b00  | Applies to all Guest OS and Hypervisor |
| Stage     | 0b00  | Reserved, set to 0                     |
| Leaf      | 0b0   | Reserved, set to 0                     |

All supported PICI operations are shown in Table B8.18.

Table B8.18: Physical Instruction Cache Invalidate operations

| Operation                                         | Arm  | Security | VIV  | AddrV |
|---------------------------------------------------|------|----------|------|-------|
| PICI all Root, Realm, Secure and Non-secure       | v9.2 | 0b00     | 0b00 | 0b0   |
| PICI by PA without Virtual Index, Root only       | v9.2 | 0b00     | 0b00 | 0b1   |
| PICI by PA with Virtual Index, Root only          | v9.2 | 0b00     | 0b11 | 0b1   |
| PICI all Realm and Non-secure                     | v9.2 | 0b01     | 0b00 | 0b0   |
| PICI by PA without Virtual Index, Realm only      | v9.2 | 0b01     | 0b00 | 0b1   |
| PICI by PA with Virtual Index, Realm only         | v9.2 | 0b01     | 0b11 | 0b1   |
| PICI all Secure and Non-secure                    | v7   | 0b10     | 0b00 | 0b0   |
| PICI by PA without Virtual Index, Secure only     | v7   | 0b10     | 0b00 | 0b1   |
| PICI by PA with Virtual Index, Secure only        | v7   | 0b10     | 0b11 | 0b1   |
| PICI all, Non-secure only                         | v7   | 0b11     | 0b00 | 0b0   |
| PICI by PA without Virtual Index, Non-secure only | v7   | 0b11     | 0b00 | 0b1   |
| PICI by PA with Virtual Index, Non-secure only    | v7   | 0b11     | 0b11 | 0b1   |

> **_NOTE:_** When VIV is 0b11, VI[19:12] is used as part of the PA.

#### B8.4.5.2 Virtual Instruction Cache Invalidate

This section describes the Virtual Instruction Cache Invalidate (VICI) operations.

The fixed field values for a VICI message are shown in Table B8.19.