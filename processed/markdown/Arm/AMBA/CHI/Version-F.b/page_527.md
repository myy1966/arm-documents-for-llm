## C3.1 Changes between Issue A and Issue B

Table C3.1: Changes between Issue A and Issue B

| Change                           | Location |
|----------------------------------|----------|
| No changes, first public release | -        |

## C3.2 Changes between Issue B and Issue C

Table C3.2: Changes between Issue B and Issue C

| Change                                                                                                                                    | Location                                                        |
|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| New feature: Response after receiving first Data packet                                                                                   | B2.3.1.1 Allocating Read                                        |
| New feature: Response after receiving first Data packet                                                                                   | B2.3.1.2 Non-allocating Read                                    |
| New feature: Separate Non-data and Data-only response                                                                                     | B2.3.1 Read transactions and multiple related locations         |
| New feature: Combined CompAck with WriteData                                                                                              | B2.5.3.3 WriteUnique transaction and multiple related locations |
| Clarification: Regarding BE bits for Write transactions                                                                                   | B2.8.3 Byte Enables                                             |
| Update: Concerning the list of fields that can change value from the original request in the retried request                              | B2.9 Request Retry                                              |
| Clarification: Concerning the transaction responses permitted to be sent to the same address when a Snoop transaction response is pending | B4.11.1 At the RN-F node                                        |
| Additional information: Concerning Legal RespErr field values for WriteDataCancel                                                         | Table B9.8                                                      |
| Clarification: Regarding TraceTag field value propagation                                                                                 | B11.7.1 TraceTag usage and rules                                |
| Corrections and additions: Concerning message field mappings                                                                              | Table C1.3, Table C1.8, and Table C1.9                          |

## C3.3 Changes between Issue C and Issue D

Table C3.3: Changes between Issue C and Issue D

| Change                                             | Location                     |
|----------------------------------------------------|------------------------------|
| New feature: Persistent CMO with two part response | B2.3.5 Dataless transactions |
|                                                    | B2.5.2 Dataless transactions |
|                                                    | Continued on next page       |