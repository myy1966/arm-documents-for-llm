Table B13.35 Continued from previous page

| Response type                               | Resp[2:0]     | State  | Notes                                                                                                            |
|---------------------------------------------|---------------|--------|------------------------------------------------------------------------------------------------------------------|
| WriteData responses                         | 0b110         | UD\_PD | State of the cache line at the RN-F when data is sent. Responsibility for updating memory is passed to the Home. |
| WriteData responses                         | 0b111         | SD\_PD | State of the cache line at the RN-F when data is sent. Responsibility for updating memory is passed to the Home. |
| CompAck responses for CopyBack transactions | 0b000         | I      | Cache state in the response is imprecise and must be ignored                                                     |
| CompAck responses for CopyBack transactions | 0b001         | SC     | State of the cache line at the RN-F when the response is sent                                                    |
| CompAck responses for CopyBack transactions | 0b010         | UC     | State of the cache line at the RN-F when the response is sent                                                    |
| CompAck responses for CopyBack transactions | 0b011         | -      | Reserved                                                                                                         |
| CompAck responses for CopyBack transactions | 0b100         | -      | Reserved                                                                                                         |
| CompAck responses for CopyBack transactions | 0b101         | -      | Reserved                                                                                                         |
| CompAck responses for CopyBack transactions | 0b110         | UD\_PD | State of the cache line at the RN-F when data is sent. Responsibility for updating memory is passed to the Home. |
| CompAck responses for CopyBack transactions | 0b111         | SD\_PD | State of the cache line at the RN-F when data is sent. Responsibility for updating memory is passed to the Home. |
| TagMatch responses                          | 0b000         | Fail   | Part of TagMatch operation                                                                                       |
| TagMatch responses                          | 0b001         | Pass   | Part of TagMatch operation                                                                                       |
| TagMatch responses                          | 0b010 - 0b111 | -      | Reserved                                                                                                         |

### B13.10.49 Forward State, FwdState

This field indicates the state in the CompData sent from the Snoopee to the Requester. Applicable in SnpRespFwded and SnpRespDataFwded, inapplicable in all other Snoop responses and must be set to 0.

Table B13.36 shows the FwdState value encodings.

Table B13.36: FwdState value encodings

| FwdState    | Description                                                                                                                                                                   |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FwdState[2] | Pass Dirty. </br> **0** Forwarded data is not Dirty. </br> **1** Forwarded data is Dirty and the responsibility of writing back the cache line is passed on to the Requester. |

Continued on next page
