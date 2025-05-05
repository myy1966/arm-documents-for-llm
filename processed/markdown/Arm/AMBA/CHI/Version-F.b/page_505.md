- When asserted, requests with MTE can be sent beyond the interface.
- When deasserted, requests with MTE must not be sent beyond the interface.

The BROADCASTMTE signal is typically deasserted when the interface does not support MTE functionality.

When the BROADCASTMTE signal is deasserted, all other MTE-related interface pins must be tied to 0. The interconnect is permitted, but not required, to remove the related MTE transport wires.

The interface fields that can be fixed to a value of 0 are:

- On DAT channels:

    - TagOp, Tag, and TU

- On REQ and RSP channels:

    - TagOp

### B16.2.7 BROADCASTERTLBIINNER and BROADCASTTLBIOUTER

The **BROADCASTTLBIINNER** (BTI) and **BROADCASTTLBIOUTER** (BTO) signals are used to control the issuing of TLBI operations in the interconnect.

Table B16.19 shows the permitted BTI and BTO signal encodings.

Table B16.19: BTI and BTO signal encodings

| BTI | BTO | Permitted |
|-----|-----|-----------|
| 0   | 0   | Yes       |
| 0   | 1   | Yes       |
| 1   | 0   | Reserved  |
| 1   | 1   | Yes       |

> **_NOTE:_** The decision to broadcast a DVM(Sync) does not only depend on the values of BTI and BTO but must also consider if any DVM operations other than TLBI must be pushed to their completion by the DVM(Sync).

### B16.2.8 BROADCASTCMOPOPA

The **BROADCASTCMOPOPA** signal is used to control the issuing of CleanInvalidPoPA Cache Maintenance Operations. The **BROADCASTCMOPOPA** signal is optional.

When the **BROADCASTCMOPOPA** signal is present and deasserted, a CleanInvalidPoPA transaction is converted to CleanInvalid. This conversion applies to both standalone PoPA Cache Maintenance Operations and Combined Write transactions.

> **_NOTE:_** The issuing of CleanInvalid transactions is further controlled by **BROADCASTINNER**, **BROADCASTOUTER**, and **BROADCASTCACHEMAINT** signals.