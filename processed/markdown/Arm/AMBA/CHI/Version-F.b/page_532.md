## C3.5 Changes between Issue E.a and Issue E.b

Table C3.5: Changes between Issue E.a and Issue E.b

| Change                                                                                                                 | Location                                      |
|------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| Update: All offensive terminology has been replaced per Arm's commitment to progressive terminology                    | Throughout the specification                  |
| Update: Restructured and reformatted Transcation structures section                                                    | B2.3 Transaction structure                    |
| Clarification: SnpAttr bit reuse in DVMOp and inapplicability in PrefetchTgt                                           | Table B2.13                                   |
| Update: SLCRepHint value is permitted to be different in the resent request                                            | B2.9 Request Retry                            |
| Clarification: Simultaneous pending of CMO and allocating requests to the same address                                 | B4.2.2.1 Cache Maintenance transactions       |
| Correction: Request Order permitted in WriteNoSnpZero from HN-I to SN-I                                                | B4.2.3.1 Immediate transactions               |
| Update: Re-write of transactions, grouping common characteristics                                                      | B4.2 Request types                            |
| Clarification: Permitted attribute values for requests, initial cache state at the Requester, and final cache state at | B4.2 Request types                            |
| Correction: Order field value 0b00 and 0b01 permitted in ReadNoSnp ᵃ                                                   | B2.3.1 Read transactions                      |
| Correction: Security field 0b10 in PCI DVM operation expanded to include both Secure and Non-secure                    | Table B8.5                                    |
| Clarification: Corrupt data must be marked with Poison, DERR, or NDERR                                                 | B9.1.4 Error response use by transaction type |
| Clarification: Poison on MTE is not supported                                                                          | B9.2.1 Poison                                 |
|                                                                                                                        | B12.11.2 Non-Tag Match errors                 |
| Correction: Legal RespErr field tables corrected                                                                       | Table B9.7                                    |
| Correction: Transaction error cannot be indicated in DBIDResp response                                                 | Table B9.7                                    |
| Update: All four combinations of Request NS and MPAMNS field values are legal ᵇ                                        | B11.4.1 MPAMSP                                |
| Clarification: MTE fields are inapplicable and must be set to 0 in WriteDataCancel write data response                 | B12.5.2 TagOp, TU, and tags relationship      |
| Update: Redundant GroupIDExt field definition is removed from the specification                                        | B13.10 Protocol flit fields                   |
| Clarification: Re-write of protocol flit fields                                                                        | B13.10 Protocol flit fields                   |

Continued on next page