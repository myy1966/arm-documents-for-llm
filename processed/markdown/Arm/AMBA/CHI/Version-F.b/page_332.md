Table B8.1 Continued from previous page

| Field name                                   | Restriction                                                                   |
|----------------------------------------------|-------------------------------------------------------------------------------|
| Order                                        | Must be all zeros.                                                            |
| PCrdType                                     | Must be all zeros if AllowRetry is asserted, otherwise the Credit type value. |
| MemAttr                                      | Must be all zeros.                                                            |
| SnpAttr </br> DoDWT                          | None. Can take any value. See DVM domain.                                     |
| PGroupID </br> StashGroupID </br> TagGroupID | Not applicable. Must be all zeros.                                            |
| LPID                                         | None. Can take any value.                                                     |
| Excl </br> SnoopMe </br> CAH                 | Must be 0.                                                                    |
| ExpCompAck                                   | Must be 0.                                                                    |
| TagOp                                        | Must be 0.                                                                    |
| TraceTag                                     | None.                                                                         |
| MPAM                                         | Must be all zeros.                                                            |
| PBHA                                         | Must be all zeros.                                                            |
| RSVDC                                        | None. Can take any value.                                                     |

### B8.3.2 Response DVMOp field value restrictions

Table B8.2 shows the Response DBIDResp, SnpResp, and Comp and CompDBIDResp message field value restrictions during a DVMOp transaction.

Table B8.2: Restrictions for response message field values during DVMOp

| Field | DBIDResp messages                                             | Comp and CompDBIDResp messages                                | SnpResp messages                                             |
|-------|---------------------------------------------------------------|---------------------------------------------------------------|--------------------------------------------------------------|
| QoS   | None. Can take any value.                                     | None. Can take any value.                                     | None. Can take any value.                                    |
| TgtID | Must be ID of the original Requester                          | Must be ID of the original Requester                          | Must be ID of the Miscellaneous Node that is handling DVMOps |
| SrcID | Must be ID of the Miscellaneous Node that is handling DVMOps. | Must be ID of the Miscellaneous Node that is handling DVMOps. | Must be the node ID that is responding to snoops             |
| TxnID | Must match TxnID of the original request                      | Must match TxnID of the original request                      | Must match the TxnID of the SnpDVMOp snoop request           |

Continued on next page
