Table B8.12 Continued from previous page

| Operation                                        | Arm  | Exception | Security | VMIDV | ASIDV | Leaf | Stage | AddrV |
|--------------------------------------------------|------|-----------|----------|-------|-------|------|-------|-------|
| Secure Guest OS TLBI by ASID and VA, Leaf only   | v8.4 | 0b10      | 0b10     | 0b1   | 0b1   | 0b1  | 0b00  | 0b1   |
| All OS TLBI all                                  | v7   | 0b10      | 0b11     | 0b0   | 0b0   | 0b0  | 0b00  | 0b0   |
| Guest OS TLBI all, Stage 1 and 2                 | v7   | 0b10      | 0b11     | 0b1   | 0b0   | 0b0  | 0b00  | 0b0   |
| Guest OS TLBI by VA                              | v7   | 0b10      | 0b11     | 0b1   | 0b0   | 0b0  | 0b00  | 0b1   |
| Guest OS TLBI all, Stage 1 only                  | v8   | 0b10      | 0b11     | 0b1   | 0b0   | 0b0  | 0b01  | 0b0   |
| Guest OS TLBI by IPA                             | v8   | 0b10      | 0b11     | 0b1   | 0b0   | 0b0  | 0b10  | 0b1   |
| Guest OS TLBI by VA, Leaf only                   | v8   | 0b10      | 0b11     | 0b1   | 0b0   | 0b1  | 0b00  | 0b1   |
| Guest OS TLBI by IPA, Leaf only                  | v8   | 0b10      | 0b11     | 0b1   | 0b0   | 0b1  | 0b10  | 0b1   |
| Guest OS TLBI by ASID                            | v7   | 0b10      | 0b11     | 0b1   | 0b1   | 0b0  | 0b00  | 0b0   |
| Guest OS TLBI by ASID and VA                     | v7   | 0b10      | 0b11     | 0b1   | 0b1   | 0b0  | 0b00  | 0b1   |
| Guest OS TLBI by ASID and VA, Leaf only          | v8   | 0b10      | 0b11     | 0b1   | 0b1   | 0b1  | 0b00  | 0b1   |
| Secure Hypervisor TLBI all                       | v8.4 | 0b11      | 0b10     | 0b0   | 0b0   | 0b0  | 0b00  | 0b0   |
| Secure Hypervisor TLBI by VA                     | v8.4 | 0b11      | 0b10     | 0b0   | 0b0   | 0b0  | 0b00  | 0b1   |
| Secure Hypervisor TLBI by VA, Leaf only          | v8.4 | 0b11      | 0b10     | 0b0   | 0b0   | 0b1  | 0b00  | 0b1   |
| Secure Hypervisor TLBI by ASID                   | v8.4 | 0b11      | 0b10     | 0b0   | 0b1   | 0b0  | 0b00  | 0b0   |
| Secure Hypervisor TLBI by ASID and VA            | v8.4 | 0b11      | 0b10     | 0b0   | 0b1   | 0b0  | 0b00  | 0b1   |
| Secure Hypervisor TLBI by ASID and VA, Leaf only | v8.4 | 0b11      | 0b10     | 0b0   | 0b1   | 0b1  | 0b00  | 0b1   |
| Hypervisor TLBI all                              | v7   | 0b11      | 0b11     | 0b0   | 0b0   | 0b0  | 0b00  | 0b0   |
| Hypervisor TLBI by VA                            | v7   | 0b11      | 0b11     | 0b0   | 0b0   | 0b0  | 0b00  | 0b1   |
| Hypervisor TLBI by VA, Leaf only                 | v8   | 0b11      | 0b11     | 0b0   | 0b0   | 0b1  | 0b00  | 0b1   |
| Hypervisor TLBI by ASID                          | v8.1 | 0b11      | 0b11     | 0b0   | 0b1   | 0b0  | 0b00  | 0b0   |
| Hypervisor TLBI by ASID and VA                   | v8.1 | 0b11      | 0b11     | 0b0   | 0b1   | 0b0  | 0b00  | 0b1   |
| Hypervisor TLBI by ASID and VA, Leaf only        | v8.1 | 0b11      | 0b11     | 0b0   | 0b1   | 0b1  | 0b00  | 0b1   |
| Realm TLBI all                                   | v9.2 | 0b10      | 0b00     | 0b0   | 0b0   | 0b0  | 0b00  | 0b0   |
| Realm Guest OS TLBI all, Stage 1 only            | v9.2 | 0b10      | 0b00     | 0b1   | 0b0   | 0b0  | 0b01  | 0b0   |
| Realm Guest OS TLBI all, Stage 1 and 2           | v9.2 | 0b10      | 0b00     | 0b1   | 0b0   | 0b0  | 0b00  | 0b0   |
| Realm Guest OS TLBI by VA                        | v9.2 | 0b10      | 0b00     | 0b1   | 0b0   | 0b0  | 0b00  | 0b1   |
| Realm Guest OS TLBI by VA, Leaf only             | v9.2 | 0b10      | 0b00     | 0b1   | 0b0   | 0b1  | 0b00  | 0b1   |
| Realm Guest OS TLBI by ASID                      | v9.2 | 0b10      | 0b00     | 0b1   | 0b1   | 0b0  | 0b00  | 0b0   |
| Realm Guest OS TLBI by ASID and VA               | v9.2 | 0b10      | 0b00     | 0b1   | 0b1   | 0b0  | 0b00  | 0b1   |

Continued on next page