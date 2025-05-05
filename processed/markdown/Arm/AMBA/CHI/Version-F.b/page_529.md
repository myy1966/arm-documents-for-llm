Table C3.3 Continued from previous page

| Change                                                                         | Location                      |
|--------------------------------------------------------------------------------|-------------------------------|
| Clarification: Regarding when the DataPull bit is set in a SnpRespData message | B13.10.37 Data Pull, DataPull |

## C3.4 Changes between Issue D and Issue E.a

Table C3.4: Changes between Issue D and Issue E.a

| Change                                                   | Location                                  |
|----------------------------------------------------------|-------------------------------------------|
| New feature: Write with optional Data:                   | B2.3.2.3 CopyBack Write                   |
| WriteEvictOrEvict                                        | B4.2.3.2 CopyBack transactions            |
|                                                          | Chapter B9 Error Handling                 |
|                                                          | Chapter B12 Memory Tagging                |
| New feature: Write Zero with no Data:                    | B2.3.2.1 Immediate Write                  |
| WriteNoSnpZero                                           | B2.6.5 Transaction ordering               |
| WriteUniqueZero                                          | B4.2.3 Write transactions                 |
|                                                          | Chapter B9 Error Handling                 |
|                                                          | Chapter B12 Memory Tagging                |
| New feature: SnpQuery Snoop request                      | B4.3 Snoop request types                  |
|                                                          | Chapter B9 Error Handling                 |
| New feature: DBIDRespOrd response                        | B2.3.2.1 Immediate Write                  |
|                                                          | B4.5.4 Miscellaneous response             |
| New feature: New transactions to support Exclusive reads | B2.3.1 Read transactions                  |
| ReadPreferUnique                                         | B2.3.4 Stash transactions                 |
| SnpPreferUnique                                          | B4.2.1 Read transactions                  |
| SnpPreferUniqueFwd                                       | B4.3 Snoop request types                  |
| MakeReadUnique                                           | B4.7.1.1 MakeReadUnique transaction       |
| MakeReadUnique(Excl)                                     | B6.3 Exclusive transactions               |
|                                                          | B6.3.1.1 MakeReadUnique(Excl)             |
|                                                          | Chapter B9 Error Handling                 |
|                                                          | Chapter B12 Memory Tagging                |
| New feature: Direct Write-data transfer                  | B2.3.2 Write transactions                 |
|                                                          | B13.10.26 Do Direct Write Transfer, DoDWT |
| New feature: Combined Write transaction                  | B1.4 Transaction classification           |

Continued on next page