Table B4.43 – Continued from previous page

| Request type      | Initial state at Requester | State before WriteData or CompAck responses ᵃ | Final state | Comp response | WriteData or CompAck response |
|-------------------|----------------------------|-----------------------------------------------|-------------|---------------|-------------------------------|
| WriteCleanFull    | UD, SD                     | SD                                            | SC          | CompDBIDResp  | CBWrData\_SD\_PD              |
| WriteCleanFull    | UD, SD                     | SD                                            | SC          | Comp ᵇ        | CompAck\_SD\_PD               |
| WriteCleanFull    | UD, SD                     | SC                                            | SC          | CompDBIDResp  | CBWrData\_SC                  |
| WriteCleanFull    | UD, SD                     | SC                                            | SC          | CompDBIDResp  | CBWrData\_I                   |
| WriteCleanFull    | UD, SD                     | SC                                            | SC          | Comp ᵇ        | CompAck\_SC                   |
| WriteCleanFull    | UD, SD                     | SC                                            | SC          | Comp ᵇ        | CompAck\_I                    |
| WriteCleanFull    | UD, SD                     | I                                             | I           | CompDBIDResp  | CBWrData\_I                   |
| WriteCleanFull    | UD, SD                     | I                                             | I           | Comp ᵇ        | CompAck\_I                    |
| WriteEvictFull    | UC                         | UC                                            | I           | CompDBIDResp  | CBWrData\_UC                  |
| WriteEvictFull    | UC                         | UC                                            | I           | Comp ᵇ        | CompAck\_UC                   |
| WriteEvictFull    | UC                         | SC                                            | I           | CompDBIDResp  | CBWrData\_SC                  |
| WriteEvictFull    | UC                         | SC                                            | I           | Comp ᵇ        | CompAck\_SC                   |
| WriteEvictFull    | UC                         | I                                             | I           | CompDBIDResp  | CBWrData\_I                   |
| WriteEvictFull    | UC                         | I                                             | I           | Comp ᵇ        | CompAck\_I                    |
| WriteEvictOrEvict | UC                         | UC ᶜ                                          | I           | CompDBIDResp  | CBWrData\_UC                  |
| WriteEvictOrEvict | UC                         | UC ᶜ                                          | I           | Comp ᵇ        | CompAck\_UC                   |
| WriteEvictOrEvict | UC, SC                     | SC                                            | I           | CompDBIDResp  | CBWrData\_SC                  |
| WriteEvictOrEvict | UC, SC                     | SC                                            | I           | Comp ᵇ        | CompAck\_SC                   |
| WriteEvictOrEvict | UC, SC                     | I                                             | I           | CompDBIDResp  | CBWrData\_I                   |
| WriteEvictOrEvict | UC, SC                     | I                                             | I           | Comp ᵇ        | CompAck\_I                    |

- ᵃ A snoop could be received while a write is pending and results in a cache line state change before the WriteData or CompAck response.
- ᵇ Comp is sent if the Home decides not to request data.
- ᶜ Once the request is sent the Requester is permitted to keep the cache state in UC but must not modify the cache line.

> **_NOTE:_** After completion of a WriteClean transaction, the cache line could be in a Unique state to immediately transition to a Dirty state.

### B4.7.4 Atomic transactions

Table B4.44 shows the cache state transitions at the Requester, and the completion and response for Atomic transactions.