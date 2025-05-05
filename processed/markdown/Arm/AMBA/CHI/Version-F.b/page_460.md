Table B13.33: RespErr value encodings

| RespErr[1:0] | Description                                                                                                                                                                                                                            |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0b00         | Normal Okay. Indicates that either: </br> - The Normal access was successful. For WriteNoSnpDef, RespErr must be used in combination with Resp to establish the exact response. See Table B13.35. </br> - The Exclusive access failed. |
| 0b01         | Exclusive Okay. Indicates that either the read or write portion of an Exclusive access was successful.                                                                                                                                 |
| 0b10         | Data Error, DERR                                                                                                                                                                                                                       |
| 0b11         | Non-data Error, NDERR                                                                                                                                                                                                                  |

### B13.10.48 Response status, Resp

This field must have the same value in all data flits of a multi-flit data transfer.

Table B13.34 shows the Resp value encodings.

Table B13.34: Resp value encodings

| Resp[2:0] | Description                                                                                                                                                                                                                                                                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Resp[2]   | PassDirty. Indicates that the data included in the response message is Dirty with respect to memory and that the responsibility of writing back the cache line is being passed to the recipient of the response message. </br> **0** Returned data is not Dirty. </br> **1** Returned data is Dirty and the responsibility of writing back the cache line is being passed on. |
| Resp[1:0] | For snoop responses, this field indicates the final state of the snooped RN-F. For completion responses, this field indicates the final state in the Request Node. For WriteData responses, this field indicates the state of the data in the Request Node when the data is sent. For TagMatch responses, Resp[0] alone indicates a Tag Match pass or fail.                   |

Table B13.35 shows the valid Resp value encodings.

Table B13.35: Valid Resp value encodings for different message types

| Response type   | Resp[2:0] | State  | Notes                           |
|-----------------|-----------|--------|---------------------------------|
| Snoop responses | 0b000     | I      | Final state of the snooped RN-F |
| Snoop responses | 0b001     | SC     | Final state of the snooped RN-F |
| Snoop responses | 0b010     | UC, UD | Final state of the snooped RN-F |

Continued on next page