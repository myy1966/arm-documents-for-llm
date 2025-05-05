Table B13.13 Continued from previous page

| Opcode[5:3] | Opcode[5:3] | Opcode[2:0] | Operation |
|-------------|-------------|-------------|-----------|
| AtomicStore | AtomicLoad  |             |           |
| 101         | 110         | 101         | SMIN      |
| 101         | 110         | 110         | UMAX      |
| 101         | 110         | 111         | UMIN      |

#### B13.10.18.2 RSP channel opcodes

Table B13.14 shows the opcodes for the Response channel.

Table B13.14: RSP channel opcodes

| Opcode[4:0] | Response       |
|-------------|----------------|
| 0x0         | RespLCrdReturn |
| 0x1         | SnpResp        |
| 0x2         | CompAck        |
| 0x3         | RetryAck       |
| 0x4         | Comp           |
| 0x5         | CompDBIDResp   |
| 0x6         | DBIDResp       |
| 0x7         | PCrdGrant      |
| 0x8         | ReadReceipt    |
| 0x9         | SnpRespFwded   |
| 0xA         | TagMatch       |
| 0xB         | RespSepData    |
| 0xC         | Persist        |
| 0xD         | CompPersist    |
| 0xE         | DBIDRespOrd    |
| 0xF         | Reserved       |
| 0x10        | StashDone      |
| 0x11        | CompStashDone  |
| 0x12 - 0x13 | Reserved       |
| 0x14        | CompCMO        |
| 0x15 - 0x1F | Reserved       |