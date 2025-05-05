- Check signals must be driven correctly in every cycle that the Check Enable term is True, see Table B9.18.
- Parity signals must be driven appropriate to all the bits in the associated payload, irrespective of whether those bits are applicable.

### B9.3.2 Error detection behavior

This specification is not prescriptive regarding component or system behavior when a parity error is detected. Depending on the system and affected signals, a flipped bit can have a wide range of effects. A flipped bit could:

- Be harmless
- Cause performance issues
- Cause data corruption
- Cause security violations
- Cause a deadlock

Also, an error on one signal could also cause parity failure on other signals.

When an error is detected, the receiver has options to:

- Terminate or propagate the transaction. It is permitted, but not required, to be protocol-compliant when the transaction is terminated.
- Correct the parity check signal or propagate the error.
- Update its memory or leave untouched. It is permitted, but not required, to mark the location as poisoned.
- Signal an error response through other means, for example, with an interrupt.

### B9.3.3 Interface parity check signals

Table B9.18 shows the parity check signals and their properties on each of the channels.

Table B9.18: Interface parity check signals

| Channel   | Check signal       | Signals covered   | Check signal width   | Check granularity   | Check enable   |
|-----------|--------------------|-------------------|----------------------|---------------------|----------------|
| Common    | SYSCOREQCHK        | SYSCOREQ          | 1                    | 1                   | RESETn == 1    |
| Common    | SYSCOACKCHK        | SYSCOACK          | 1                    | 1                   | RESETn == 1    |
| Common    | TXSACTIVECHK       | TXSACTIVE         | 1                    | 1                   | RESETn == 1    |
| Common    | RXSACTIVECHK       | RXSACTIVE         | 1                    | 1                   | RESETn == 1    |
| Common    | TXLINKACTIVEREQCHK | TXLINKACTIVEREQ   | 1                    | 1                   | RESETn == 1    |
| Common    | TXLINKACTIVEACKCHK | TXLINKACTIVEACK   | 1                    | 1                   | RESETn == 1    |
| Common    | RXLINKACTIVEREQCHK | RXLINKACTIVEREQ   | 1                    | 1                   | RESETn == 1    |
| Common    | RXLINKACTIVEACKCHK | RXLINKACTIVEACK   | 1                    | 1                   | RESETn == 1    |
| REQ       | REQFLITPENDCHK     | REQFLITPEND       | 1                    | 1                   | RESETn == 1    |
| REQ       | REQFLITVCHK        | REQFLITV          | 1                    | 1                   | RESETn == 1    |
| REQ       | REQFLITCHK         | REQFLIT           | ceil(R/8) ᵃ          | 1 to 8              | REQFLITV == 1  |
| REQ       | REQLCRDVCHK        | REQLCRDV          | 1                    | 1                   | RESETn == 1    |
| RSP       | RSPFLITPENDCHK     | RSPFLITPEND       | 1                    | 1                   | RESETn == 1    |
| RSP       | RSPFLITVCHK        | RSPFLITV          | 1                    | 1                   | RESETn == 1    |
| RSP       | RSPFLITCHK         | RSPFLIT           | ceil(T/8) ᵇ          | 1 to 8              | RSPFLITV == 1  |
| RSP       | RSPLCRDVCHK        | RSPLCRDV          | 1                    | 1                   | RESETn == 1    |

Continued on next page