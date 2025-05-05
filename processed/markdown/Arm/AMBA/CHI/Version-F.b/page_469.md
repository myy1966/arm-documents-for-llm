## B14.1 Clock and initialization

This section specifies the CHI requirement for global clock and reset signals.

### B14.1.1 Clock

This specification does not define a specific clocking microarchitecture. It is expected that all devices, interconnects, and so on, includes one or more clocks that can be relied upon by other Link layer functions that require synchronous communication. A generic clock signal is referred to as CLK in the following sections, where applicable.

### B14.1.2 Reset

This specification does not define a specific reset microarchitecture. It is expected that all devices, interconnects, and so on, include a specific reset deassertion event that can be relied upon by other Link layer functions. A generic reset signal is referred to as RESETn in the following sections, where applicable.

### B14.1.3 Initialization

During reset the following interface signals must be deasserted by the component:

- **TX\*\*\*LCRDV**
- **TX\*\*\*FLITV**
- **TXLINKACTIVEREQ** and **RXLINKACTIVEACK**

The earliest point after reset that the component is permitted to begin driving these signals HIGH is at a rising CLK edge after RESETn is HIGH.

All other signals can take any value.