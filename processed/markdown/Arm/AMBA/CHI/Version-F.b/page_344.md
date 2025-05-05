### B8.4.3 TLB Invalidate

This section details the TLB Invalidate (TLBI) message.

For a TLBI message, some fields have a fixed value, as shown in Table B8.11

Table B8.11: Fixed field values for a TLBI message

| Field   | Value | Status |
|---------|-------|--------|
| DVMType | 0b000 | TLBI   |

The entries on which the TLBI must operate depends on the fields in the message.

Table B8.12 shows all the supported TLBI operations.

The Arm column indicates the minimum Arm architecture version required to support the message.

Table B8.12: TLBI messages

| Operation                                         | Arm  | Exception | Security | VMIDV | ASIDV | Leaf | Stage | AddrV |
|---------------------------------------------------|------|-----------|----------|-------|-------|------|-------|-------|
| EL3 TLBI all                                      | v8   | 0b01      | 0b10     | 0b0   | 0b0   | 0b0  | 0b00  | 0b0   |
| EL3 TLBI by VA                                    | v8   | 0b01      | 0b10     | 0b0   | 0b0   | 0b0  | 0b00  | 0b1   |
| EL3 TLBI by VA, Leaf only                         | v8   | 0b01      | 0b10     | 0b0   | 0b0   | 0b1  | 0b00  | 0b1   |
| Secure Guest OS TLBI by Non-secure IPA            | v8.4 | 0b10      | 0b01     | 0b1   | 0b0   | 0b0  | 0b10  | 0b1   |
| Secure Guest OS TLBI by Non-secure IPA, Leaf only | v8.4 | 0b10      | 0b01     | 0b1   | 0b0   | 0b1  | 0b10  | 0b1   |
| Secure TLBI all                                   | v7   | 0b10      | 0b10     | 0b0   | 0b0   | 0b0  | 0b00  | 0b0   |
| Secure TLBI by VA                                 | v7   | 0b10      | 0b10     | 0b0   | 0b0   | 0b0  | 0b00  | 0b1   |
| Secure TLBI by VA, Leaf only                      | v8   | 0b10      | 0b10     | 0b0   | 0b0   | 0b1  | 0b00  | 0b1   |
| Secure TLBI by ASID                               | v7   | 0b10      | 0b10     | 0b0   | 0b1   | 0b0  | 0b00  | 0b0   |
| Secure TLBI by ASID and VA                        | v7   | 0b10      | 0b10     | 0b0   | 0b1   | 0b0  | 0b00  | 0b1   |
| Secure TLBI by ASID and VA, Leaf only             | v8   | 0b10      | 0b10     | 0b0   | 0b1   | 0b1  | 0b00  | 0b1   |
| Secure Guest OS TLBI all                          | v8.4 | 0b10      | 0b10     | 0b1   | 0b0   | 0b0  | 0b00  | 0b0   |
| Secure Guest OS TLBI by VA                        | v8.4 | 0b10      | 0b10     | 0b1   | 0b0   | 0b0  | 0b00  | 0b1   |
| Secure Guest OS TLBI all, Stage 1 only            | v8.4 | 0b10      | 0b10     | 0b1   | 0b0   | 0b0  | 0b01  | 0b0   |
| Secure Guest OS TLBI by Secure IPA                | v8.4 | 0b10      | 0b10     | 0b1   | 0b0   | 0b0  | 0b10  | 0b1   |
| Secure Guest OS TLBI by VA, Leaf only             | v8.4 | 0b10      | 0b10     | 0b1   | 0b0   | 0b1  | 0b00  | 0b1   |
| Secure Guest OS TLBI by Secure IPA, Leaf only     | v8.4 | 0b10      | 0b10     | 0b1   | 0b0   | 0b1  | 0b10  | 0b1   |
| Secure Guest OS TLBI by ASID                      | v8.4 | 0b10      | 0b10     | 0b1   | 0b1   | 0b0  | 0b00  | 0b0   |
| Secure Guest OS TLBI by ASID and VA               | v8.4 | 0b10      | 0b10     | 0b1   | 0b1   | 0b0  | 0b00  | 0b1   |

Continued on next page