#### B13.10.18.3 SNP channel opcodes

Table B13.15 shows the opcodes for the Snoop channel.

Table B13.15: SNP channel opcodes

| Opcode[4:0] | Snoop command        |
|-------------|----------------------|
| 0x00        | SnpLCrdReturn        |
| 0x01        | SnpShared            |
| 0x02        | SnpClean             |
| 0x03        | SnpOnce              |
| 0x04        | SnpNotSharedDirty    |
| 0x05        | SnpUniqueStash       |
| 0x06        | SnpMakeInvalidStash  |
| 0x07        | SnpUnique            |
| 0x08        | SnpCleanShared       |
| 0x09        | SnpCleanInvalid      |
| 0x0A        | SnpMakeInvalid       |
| 0x0B        | SnpStashUnique       |
| 0x0C        | SnpStashShared       |
| 0x0D        | SnpDVMOp             |
| 0x0E - 0x0F | Reserved             |
| 0x10        | SnpQuery             |
| 0x11        | SnpSharedFwd         |
| 0x12        | SnpCleanFwd          |
| 0x13        | SnpOnceFwd           |
| 0x14        | SnpNotSharedDirtyFwd |
| 0x15        | SnpPreferUnique      |
| 0x16        | SnpPreferUniqueFwd   |
| 0x17        | SnpUniqueFwd         |
| 0x18 - 0x1F | Reserved             |

#### B13.10.18.4 DAT channel opcodes

Table B13.16 shows the opcodes for the Data channel.