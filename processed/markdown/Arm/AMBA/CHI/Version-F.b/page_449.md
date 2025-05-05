Table B13.16: DAT channel opcodes

| Opcode[3:0] | Data command         |
|-------------|----------------------|
| 0x0         | DataLCrdReturn       |
| 0x1         | SnpRespData          |
| 0x2         | CopyBackWriteData    |
| 0x3         | NonCopyBackWriteData |
| 0x4         | CompData             |
| 0x5         | SnpRespDataPtl       |
| 0x6         | SnpRespDataFwded     |
| 0x7         | WriteDataCancel      |
| 0x8 - 0xA   | Reserved             |
| 0xB         | DataSepResp          |
| 0xC         | NCBWrDataCompAck     |
| 0xD - 0xF   | Reserved             |

### B13.10.19 Deep persistence, Deep

This field is used by the Requester to indicate that writes must have been written to the final destination before the Completer can provide certain responses.

Applicable in the CleanSharedPersist* request and Combined Write request with CleanSharedPersistSep.

Inapplicable and must be set to 0 in all other requests.

When Deep is deasserted:

- All earlier writes must have reached the PoP before thc Completer can send:

    - Comp for a CleanSharedPersist transaction
    - Persist or CompPersist for a CleanSharedPersistSep transaction

- The PoP is the point at which it is guaranteed that sufficient time is available to make the data persistent after loss of power.

When Deep is asserted:

- All earlier writes must have been written to the final destination, not just the PoP, before the Completer can send:

    - Comp for a CleanSharedPersist transaction
    - Persist or CompPersist for a CleanSharedPersistSep transaction

- The final destination is the point at which no time is required to make the data persistent after the loss of power, thus preserving data even when battery failure occurs.

See Table B2.7 for more information on response ordering guarantees.

### B13.10.20 Address, Addr

This field specifies the address associated with the message.