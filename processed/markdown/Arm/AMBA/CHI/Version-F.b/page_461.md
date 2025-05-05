Table B13.35 Continued from previous page

| Response type                                             | Resp[2:0]     | State       | Notes                                                                                              |
|-----------------------------------------------------------|---------------|-------------|----------------------------------------------------------------------------------------------------|
| Snoop responses                                           | 0b011         | SD          |                                                                                                    |
| Snoop responses                                           | 0b100         | I\_PD       | Final state of the snooped RN-F. Responsibility for updating memory is passed to Home.             |
| Snoop responses                                           | 0b101         | SC\_PD      | Final state of the snooped RN-F. Responsibility for updating memory is passed to Home.             |
| Snoop responses                                           | 0b110         | UC\_PD      | Final state of the snooped RN-F. Responsibility for updating memory is passed to Home.             |
| Snoop responses                                           | 0b111         | -           | Reserved                                                                                           |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b000         | I           | Final state of the requesting RN-F                                                                 |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b001         | SC          | Final state of the requesting RN-F                                                                 |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b010         | UC          | Final state of the requesting RN-F                                                                 |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b011         | -           | Final state of the requesting RN-F                                                                 |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b100         | -           | Reserved                                                                                           |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b101         | -           | Reserved                                                                                           |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b110         | UD\_PD      | Reserved                                                                                           |
| Comp responses (Not including WriteNoSnpDef transactions) | 0b111         | SD\_PD      | Final state of the requesting RN-F. Responsibility for updating memory is passed to the Requester. |
| Comp or CompDBIDResp responses for WriteNoSnpDef only     | 0b000         | Successful  | Only when RespErr[1:0] = 0b00                                                                      |
| Comp or CompDBIDResp responses for WriteNoSnpDef only     | 0b001         | Unsupported | Reserved and must be 0b000 when RespErr[1:0] != 0b00 </br> See Table B9.1 for more information     |
| Comp or CompDBIDResp responses for WriteNoSnpDef only     | 0b010         | Defer       | Reserved and must be 0b000 when RespErr[1:0] != 0b00 </br> See Table B9.1 for more information     |
| Comp or CompDBIDResp responses for WriteNoSnpDef only     | 0b011 - 0b111 | -           | Reserved                                                                                           |
| WriteData responses                                       | 0b000         | I           | Cache state in the response is imprecise and must be ignored                                       |
| WriteData responses                                       | 0b001         | SC          | State of the cache line at the RN-F when data is sent                                              |
| WriteData responses                                       | 0b010         | UC          | State of the cache line at the RN-F when data is sent                                              |
| WriteData responses                                       | 0b011         | -           | Reserved                                                                                           |
| WriteData responses                                       | 0b101         | -           | Reserved                                                                                           |

Continued on next page