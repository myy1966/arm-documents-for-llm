Table B13.12 Continued from previous page

| Request command |                      |                              |
|-----------------|----------------------|------------------------------|
| Opcode[5:0]     | Opcode[6] = 0        | Opcode[6] = 1                |
| 0x1D            | WriteNoSnpFull       | Reserved                     |
| 0x1E            | Reserved             | WriteCleanFullCleanShPerSep  |
| 0x1F            | Reserved             | Reserved                     |
| 0x20            | WriteUniqueFullStash | WriteNoSnpPtlCleanSh         |
| 0x21            | WriteUniquePtlStash  | WriteNoSnpPtlCleanInv        |
| 0x22            | StashOnceShared      | WriteNoSnpPtlCleanShPerSep   |
| 0x23            | StashOnceUnique      | Reserved                     |
| 0x24            | ReadOnceCleanInvalid | WriteUniquePtlCleanSh        |
| 0x25            | ReadOnceMakeInvalid  | Reserved                     |
| 0x26            | ReadNotSharedDirty   | WriteUniquePtlCleanShPerSep  |
| 0x27            | CleanSharedPersist   | Reserved                     |
| 0x28 - 0x2F     | AtomicStore          | Reserved                     |
| 0x30            | AtomicLoad           | WriteNoSnpPtlCleanInvPoPA ᵃ  |
| 0x31            | AtomicLoad           | WriteNoSnpFullCleanInvPoPA ᵃ |
| 0x32 - 0x37     | AtomicLoad           | Reserved                     |
| 0x38            | AtomicSwap           | Reserved                     |
| 0x39            | AtomicCompare        | WriteBackFullCleanInvPoPA ᵃ  |
| 0x3A            | PrefetchTgt          | Reserved                     |
| 0x3B - 0x3F     | Reserved             | Reserved                     |

- ᵃ This request was not supported prior to CHI Issue F.

Table B13.13: Sub-opcodes for AtomicStore and AtomicLoad

| Opcode[5:3] | Opcode[5:3] | Opcode[2:0] | Operation |
|-------------|-------------|-------------|-----------|
| AtomicStore | AtomicLoad  |             |           |
| 101         | 110         | 000         | ADD       |
| 101         | 110         | 001         | CLR       |
| 101         | 110         | 010         | EOR       |
| 101         | 110         | 011         | SET       |
| 101         | 110         | 100         | SMAX      |

Continued on next page