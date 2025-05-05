Table B13.36 Continued from previous page

| FwdState      | Description                                                  |
|---------------|--------------------------------------------------------------|
| FwdState[1:0] | Indicates the final state at the Requester. See Table B13.37 |

Table B13.37 enumerates the FwdState value encodings.

Table B13.37: Valid FwdState value encodings

| FwdState[2:0] | State  | Comment                                                                                     |
|---------------|--------|---------------------------------------------------------------------------------------------|
| 0b000         | I      | Final state at the Requester                                                                |
| 0b001         | SC     | Final state at the Requester                                                                |
| 0b010         | UC     | Final state at the Requester                                                                |
| 0b011         | -      | Reserved                                                                                    |
| 0b100         | -      | Reserved                                                                                    |
| 0b101         | -      | Reserved                                                                                    |
| 0b110         | UD\_PD | Final state at the Requester. Responsibility for updating memory is passed to the Requester |
| 0b111         | SD\_PD | Final state at the Requester. Responsibility for updating memory is passed to the Requester |

### B13.10.50 Completer Busy, CBusy

This field is a mechanism for the Completer of a transaction to indicate its current level of activity. The CBusy value encodings are IMPLEMENTATION DEFINED. See B11.6 Completer Busy.

### B13.10.51 Data payload, Data

This field is the data payload that is being transported in a Data packet.

The following data bus widths are supported:

- 128-bit
- 256-bit
- 512-bit

See B2.8.4 Data packetization.

### B13.10.52 Critical Chunk Identifier, CCID

This field indicates the critical 128-bit chunk of the data that is being requested. See B2.8.6 Critical Chunk Identifier.

Table B13.38 shows the CCID value encodings.