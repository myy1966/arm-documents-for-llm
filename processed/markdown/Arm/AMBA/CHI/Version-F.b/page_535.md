Table C3.7: Changes between Issue E.c and Issue F

| Change                                                                                                                 | Location                                                 |
|------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| Update: ReadOnceMakeInvalid return states enhanced to allow UD\_PD data repsonses, allowing for SnpUniqueFwd DCT flows | Chapter B4 Coherence Protocol                            |
| Update: Permitted TagOp values updated for ReadOnceMakeInvalid, ReadOnceCleanInvalid, and MakeReadUnique               | Chapter B12 Memory Tagging                               |
| Update: DataSource field extension to 5 bits                                                                           | Chapter B11 System Control, Debug, Trace, and Monitoring |
|                                                                                                                        | B13.10.57 Data source, DataSource                        |
| Update: Readonce updated to enable partial cache line read                                                             | B4.2.1 Read transactions                                 |
| New feature: Deferrable write                                                                                          | B2.3.2.1 Immediate Write                                 |
|                                                                                                                        | B4.5.1.3.1 WriteNoSnpDef                                 |
|                                                                                                                        | B2.3.2 Write transactions                                |
| New feature: CopyAtHome, CAH, bit to help reduce the write data bandwidth for CopyBack Write transactions              | B13.10.30 CopyAtHome, CAH                                |
|                                                                                                                        | B2.3.2.3 CopyBack Write                                  |
| New feature: Page-based Hardware Attribute (PBHA)                                                                      | B11.5 Page-based Hardware Attributes                     |
|                                                                                                                        | B13.10.31 Page-based Hardware Attribute, PBHA            |
|                                                                                                                        | B16.1.18 PBHA\_Support                                   |
| New feature: Realm Management Extension (RME)                                                                          | B2.7.2 Physical Address Space, PAS                       |
|                                                                                                                        | B16.1.16 RME\_Support                                    |
|                                                                                                                        | B16.2.8 BROADCASTCMOPOPA                                 |
|                                                                                                                        | Chapter B8 DVM Operations                                |
| New feature: Non-shareable and CMO                                                                                     | B16.1.17                                                 |

## C3.8 Changes between Issue F and Issue F.b

Table C3.8: Changes between Issue F and Issue F.b

| Change                                                 | Location    |
|--------------------------------------------------------|-------------|
| Defect: MPAM field width has been corrected to 12 bits | B11.4 MPAM  |
|                                                        | Table B13.8 |

Continued on next page