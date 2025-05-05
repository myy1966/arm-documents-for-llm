Table B4.41: Additional cache state transitions at the Requester for the MakeReadUnique request (Excl)

| Initial state | State at time of response | State when Home sent invalidating snoop | Final state | Comp response                      | Precise Snoop Filter | Imprecise or Absent Snoop Filter |
|---------------|---------------------------|-----------------------------------------|-------------|------------------------------------|----------------------|----------------------------------|
| SC, SD        | SC                        | No                                      | SC          | Comp\_SC                           | Y                    | -                                |
| SC, SD        | SC                        | No                                      | SC          | CompData\_SC                       | -                    | Y                                |
| SC, SD        | SC                        | No                                      | SC          | RespSepData, </br> DataSepResp\_SC | -                    | Y                                |
| SC, SD        | I                         | Yes                                     | SC          | CompData\_SC                       | Y                    | Y                                |
| SC, SD        | I                         | Yes                                     | SC          | RespSepData, </br> DataSepResp\_SC | Y                    | Y                                |
| SD            | SD                        | No                                      | SD          | Comp\_SC                           | Y                    | -                                |
| SD            | SD                        | No                                      | SD          | CompData\_SC                       | -                    | Y                                |
| SD            | SD                        | No                                      | SD          | RespSepData, </br> DataSepResp\_SC | -                    | Y                                |

See B6.3.1.1 MakeReadUnique(Excl) for additional MakeReadUnique(Excl) behavioral requirements.

### B4.7.2 Dataless request transactions

Table B4.42 shows the cache state transitions at the Requester, and the completion responses, for Dataless request transactions.

Table B4.42: Cache state transitions at the Requester for Dataless request transactions

| Request type       | Initial expected state   | Initial permitted state   | Final state   | Comp response                     |
|--------------------|--------------------------|---------------------------|---------------|-----------------------------------|
| CleanUnique        | I                        | UC, UCE                   | UCE           | Comp\_UC                           |
| CleanUnique        | SC                       | UC                        | UC            | Comp\_UC                           |
| CleanUnique        | SD                       | UD                        | UD            | Comp\_UC                           |
| MakeUnique         | I, SC, SD                | UC, UCE                   | UD            | Comp\_UC                           |
| Evict              | I                        | -                         | I             | Comp\_I                            |
| StashOnceUnique    | I                        | -                         | I             | Comp                              |
| StashOnceSepUnique | I                        | -                         | I             | Comp + StashDone or CompStashDone |
| StashOnceShared    | I                        | -                         | I             | Comp                              |
| StashOnceSepShared | I                        | -                         | I             | Comp + StashDone or CompStashDone |

Continued on next page