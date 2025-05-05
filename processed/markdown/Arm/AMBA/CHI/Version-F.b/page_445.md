#### B13.10.18.1 REQ channel opcodes

Table B13.12 shows the opcodes for the Request channel.

Table B13.12: REQ channel opcodes

| Request command |                       |                              |
|-----------------|-----------------------|------------------------------|
| Opcode[5:0]     | Opcode[6] = 0         | Opcode[6] = 1                |
| 0x00            | ReqLCrdReturn         | Reserved                     |
| 0x01            | ReadShared            | MakeReadUnique               |
| 0x02            | ReadClean             | WriteEvictOrEvict            |
| 0x03            | ReadOnce              | WriteUniqueZero              |
| 0x04            | ReadNoSnp             | WriteNoSnpZero               |
| 0x05            | PCrdReturn            | Reserved                     |
| 0x06            | Reserved              | Reserved                     |
| 0x07            | ReadUnique            | StashOnceSepShared           |
| 0x08            | CleanShared           | StashOnceSepUnique           |
| 0x09            | CleanInvalid          | Reserved                     |
| 0x0A            | MakeInvalid           | Reserved                     |
| 0x0B            | CleanUnique           | Reserved                     |
| 0x0C            | MakeUnique            | ReadPreferUnique             |
| 0x0D            | Evict                 | CleanInvalidPoPA ᵃ           |
| 0x0E            | Reserved              | WriteNoSnpDef ᵃ              |
| 0x0F            | Reserved              | Reserved                     |
| 0x10            | Reserved              | WriteNoSnpFullCleanSh        |
| 0x11            | ReadNoSnpSep          | WriteNoSnpFullCleanInv       |
| 0x12            | Reserved              | WriteNoSnpFullCleanShPerSep  |
| 0x13            | CleanSharedPersistSep | Reserved                     |
| 0x14            | DVMOp                 | WriteUniqueFullCleanSh       |
| 0x15            | WriteEvictFull        | Reserved                     |
| 0x16            | Reserved              | WriteUniqueFullCleanShPerSep |
| 0x17            | WriteCleanFull        | Reserved                     |
| 0x18            | WriteUniquePtl        | WriteBackFullCleanSh         |
| 0x19            | WriteUniqueFull       | WriteBackFullCleanInv        |
| 0x1A            | WriteBackPtl          | WriteBackFullCleanShPerSep   |
| 0x1B            | WriteBackFull         | Reserved                     |
| 0x1C            | WriteNoSnpPtl         | WriteCleanFullCleanSh        |

Continued on next page