| DataSource        | Description                                | Comments                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-------------------|--------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0bR0111           | PrefetchTgt memory prefetch was not useful | Read request went through a complete memory access. </br> The precise reason for signaling that a prefetch was not useful is IMPLEMENTATION DEFINED. </br> Note </br> A non-exhaustive list of examples of what this could signal is: - There is no latency reduction due to the PrefetchTgt request sent earlier. </br> - There was no PrefetchTgt request sent earlier. </br> - The Completer does not support the reporting of the effectiveness of a PrefetchTgt request. |
| 0bR1000 - 0bR1111 |                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

### B13.10.58 System Level Caches Replacement Hint, SLCRepHint

This field forwards cache replacement hints from the Requesters to the SLC in the interconnect. See B11.3 SLC Replacement Hint.

### B13.10.59 Reserved for Customer Use, RSVDC

This field in a Protocol flit can take any value. Propagation of this field through the interconnect is IMPLEMENTATION DEFINED. There is no defined relationship between RSDVC field values in different packets of a transaction.

This field is applicable in the REQ and DAT channels as follows:

- The presence of this field is optional.
- The permitted field widths are 4-bit, 8-bit, 12-bit, 16-bit, 24-bit, and 32-bit.
- The field widths:

    - Can be different between REQ and DAT channels.
    - Need not be the same across all REQ channels in the system.
    - Need not be the same across all DAT channels in the system.

When connecting Tx and Rx flit interfaces that have mismatched RSVDC widths:

- The corresponding lower-order bits of the RSVDC field must be connected at each side of the interface.
- The higher-order RSVDC bits at the RX interface that do not have corresponding bits at the TX interface must be tied LOW.