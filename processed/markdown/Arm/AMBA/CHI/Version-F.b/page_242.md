Table B4.40 and Table B4.41 use the following key:

- Y Yes, permitted
- \- Not permitted

Table B4.40: Cache state transitions at the Requester for the MakeReadUnique request (non-Excl and Excl)

| Initial state | State at time of response | Home sent invalidating snoop | Final state | Comp response                          | Precise Snoop Filter | Imprecise or Absent Snoop Filter | Notes                                               |
|---------------|---------------------------|------------------------------|-------------|----------------------------------------|----------------------|----------------------------------|-----------------------------------------------------|
| SD            | SD                        | No                           | UD          | Comp\_UC                               | Y                    | -                                |                                                     |
| SD            | SD                        | No                           | UD          | CompData\_UC                           | -                    | Y                                | Returned data could be stale                        |
| SD            | SD                        | No                           | UD          | RespSepData, </br> DataSepResp\_UC     | -                    | Y                                | Returned data could be stale                        |
| SC, SD        | SC                        | No                           | UC          | Comp\_UC                               | Y                    | -                                |                                                     |
| SC, SD        | SC                        | No                           | UC          | CompData\_UC                           | -                    | Y                                |                                                     |
| SC, SD        | SC                        | No                           | UC          | RespSepData, </br> DataSepResp\_UC     | -                    | Y                                |                                                     |
| SC, SD        | SC                        | No                           | UD          | Comp\_UD\_PD                           | Y                    | -                                |                                                     |
| SC, SD        | SC                        | No                           | UD          | CompData\_UD\_PD                       | -                    | Y                                | Data in response is identical to the Requester copy |
| SC, SD        | SC                        | No                           | UD          | RespSepData, </br> DataSepResp\_UD\_PD | -                    | Y                                | Data in response is identical to the Requester copy |
| SC, SD        | I                         | Yes                          | UC          | CompData\_UC                           | Y                    | Y                                | Line lost to an invalidating snoop                  |
| SC, SD        | I                         | Yes                          | UC          | RespSepData, </br> DataSepResp\_UC     | Y                    | Y                                | Line lost to an invalidating snoop                  |
| SC, SD        | I                         | Yes                          | UD          | CompData\_UD\_PD                       | Y                    | Y                                | Line lost to an invalidating snoop                  |
| SC, SD        | I                         | Yes                          | UD          | RespSepData, </br> DataSepResp\_UD\_PD | Y                    | Y                                | Line lost to an invalidating snoop                  |
| I, UC, UD     | Not permitted                                                                                                                                                                                                                   |
