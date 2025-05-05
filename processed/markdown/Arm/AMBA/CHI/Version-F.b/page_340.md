Table B8.7: Leaf entry hint for non-range TLB Invalidations

| TG   | TTL  | Meaning                                                     |
|------|------|-------------------------------------------------------------|
| 0b00 | 0b00 | No level hint                                               |
| 0b00 | 0b01 | Reserved                                                    |
| 0b00 | 0b10 | Reserved                                                    |
| 0b00 | 0b11 | Reserved                                                    |
| 0b01 | 0b00 | The leaf entry is on level 0 of the translation table walk. |
| 0b01 | 0b01 | The leaf entry is on level 1 of the translation table walk. |
| 0b01 | 0b10 | The leaf entry is on level 2 of the translation table walk. |
| 0b01 | 0b11 | The leaf entry is on level 3 of the translation table walk. |
| 0b10 | 0b00 | Reserved                                                    |
| 0b10 | 0b01 | The leaf entry is on level 1 of the translation table walk. |
| 0b10 | 0b10 | The leaf entry is on level 2 of the translation table walk. |
| 0b10 | 0b11 | The leaf entry is on level 3 of the translation table walk. |
| 0b11 | 0b00 | Reserved                                                    |
| 0b11 | 0b01 | The leaf entry is on level 1 of the translation table walk. |
| 0b11 | 0b10 | The leaf entry is on level 2 of the translation table walk. |
| 0b11 | 0b11 | The leaf entry is on level 3 of the translation table walk. |

***Security field***

The Security field has different meanings depending on the DVMType, as shown in Table B8.8.

Table B8.8: Security field encodings for each DVMType

| Security | TLBI                                   | BPI                   | PICI Invalidation All               | PICI Invalidation by PA | VICI                  |
|----------|----------------------------------------|-----------------------|-------------------------------------|-------------------------|-----------------------|
| 00       | Realm                                  | Secure and Non-secure | Root, Realm, Secure, and Non-secure | Root                    | Secure and Non-secure |
| 01       | Non-secure address from Secure context | Reserved              | Realm and Non-secure                | Realm                   | Reserved              |
| 10       | Secure                                 | Reserved              | Secure and Non-secure               | Secure                  | Secure                |
| 11       | Non-secure                             | Reserved              | Non-secure                          | Non-secure              | Non-secure            |
