Table B3.1: Source of Response packet TgtID

| Response message            | TgtID obtained from               |                                                                                            |                                                     |
|-----------------------------|-----------------------------------|--------------------------------------------------------------------------------------------|-----------------------------------------------------|
|                             | Home Node                         | Subordinate Node                                                                           | Request Node                                        |
| RetryAck                    | Request.SrcID                     | Request.SrcID                                                                              | -                                                   |
| PCrdGrant                   | Request.SrcID                     | Request.SrcID                                                                              | -                                                   |
| ReadReceipt                 | Request.SrcID                     | Request.SrcID                                                                              | -                                                   |
| RespSepData                 | Request.SrcID or SnpResp*.SrcID ᵃ | -                                                                                          | -                                                   |
| Comp                        | Request.SrcID                     | Request.SrcID                                                                              | -                                                   |
| CompCMO                     | Request.SrcID                     | Request.SrcID                                                                              | -                                                   |
| DataSepResp                 | Request.SrcID or SnpResp*.SrcID ᵃ | Request.ReturnNID                                                                          | -                                                   |
| CompData                    | Request.SrcID or SnpResp*.SrcID ᵃ | Request.ReturnNID                                                                          | Snoop.FwdNID                                        |
| CompAck (reads)             | -                                 | -                                                                                          | Comp.SrcID or RespSepData.SrcID or CompData.HomeNID |
| CompAck (writes)            | -                                 | -                                                                                          | Comp.SrcID or DBIDResp*.SrcID or CompDBIDResp.SrcID |
| CompDBIDResp                | Request.SrcID                     | Request.SrcID ᵇ                                                                            |                                                     |
| DBIDResp                    | Request.SrcID                     | If Request.DoDWT == 0 then: Request.SrcID or If Request.DoDWT == 1 then: Request.ReturnNID | -                                                   |
| DBIDRespOrd                 | Request.SrcID                     | -                                                                                          | -                                                   |
| WriteData                   | -                                 | -                                                                                          | DBIDResp*.SrcID or CompDBIDResp.SrcID               |
| NonCopyBackWriteDataCompAck | -                                 | -                                                                                          | Comp.SrcID or DBIDResp*.SrcID or CompDBIDResp.SrcID |
| Persist                     | Request.SrcID                     | Request.ReturnNID                                                                          | -                                                   |
| CompPersist                 | Request.SrcID                     | Request.SrcID ᵇ                                                                            | -                                                   |
| StashDone                   | Request.SrcID                     | -                                                                                          | -                                                   |
| CompStashDone               | Request.SrcID                     | -                                                                                          | -                                                   |
| TagMatch                    | Request.SrcID                     | Request.ReturnNID                                                                          | -                                                   |
| SnpResp* ᶜ                  | -                                 | -                                                                                          | Snoop.SrcID                                         |

- ᵃ For Data Pull requests where Snoop response can be SnpResp or SnpRespData or SnpRespDataPtl.
- ᵇ This response is only permitted when Request.SrcID = Request.ReturnNID, including when Request.DoDWT = 1.
- ᶜ SnpResp, SnpRespData, SnpRespDataPtl, SnpRespFwded, and SnpRespDataFwded.

### B3.3.3 TgtID determination for snoop request messages

A snoop request does not include a TgtID. The protocol does not define an architectural mechanism to address and send a Snoop request to a target. It is expected that the mechanism is IMPLEMENTATION DEFINED and therefore outside the scope of this specification.