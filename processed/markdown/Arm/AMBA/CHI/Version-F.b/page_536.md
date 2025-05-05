Table C3.8 Continued from previous page

| Change                                                                                                                                               | Location                                                |
|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| Relaxation: CBusy is allowed to vary within a single DAT packet                                                                                      | B2.8.4 Data packetization                               |
| Defect: CompAck and NCBWrDataCompAck behavior in OWO Immediate Writes                                                                                | B2.3.2.1 Immediate Write                                |
|                                                                                                                                                      | B2.3.2.4 Combined Immediate Write and CMO               |
|                                                                                                                                                      | B2.3.2.5 Combined Immediate Write and Persist CMO       |
| Clarification: SnpMakeInvalidStash is a permitted snoop for WriteUniquePtlStash                                                                      | Table B4.25                                             |
|                                                                                                                                                      | Table B7.1                                              |
| Clarification: Permitted cache states for ReadClean                                                                                                  | Table B4.4                                              |
|                                                                                                                                                      | Table B4.5                                              |
| Clarification: MakeReadUnique(Excl) responses for Requester in SC state                                                                              | Table B4.41                                             |
| Clarification: SnpRespData\_I cannot be sent from SC                                                                                                 | Table B4.50                                             |
|                                                                                                                                                      | B13.10.36 Return to Source, RetToSrc                    |
| Relaxation: Line update rules for CopyBack request with CAH=1                                                                                        | B2.7.8 CopyAtHome attribute                             |
| Clarification: SnpDVMOp does not need to be sent to original Requester                                                                               | B8.2.1 Non-sync type DVM transaction flow               |
| Clarification: CMO-initiated memory update should use PBHA value from SnpRespData                                                                    | B11.5.4 PBHA value consistency                          |
| Defect: Permitted SnpResp.RespErr values in SnpDVMOp                                                                                                 | Table B8.2                                              |
| Clarification: Range field value for GPT TLBI DVMOp transactions                                                                                     | B8.4.3.3 Invalidation Size in GPT TLBI by PA operations |
| Clarification: SLCRepHint not applicable for ReadNoSnpSep                                                                                            | Table C1.3                                              |
| Clarification: WriteNoSnpZero can be to Device memory                                                                                                | B2.7.3.2.1 Device memory type                           |
| Clarification: Common field non applicable bit requirements for DataPull updated to reduce gateway complexity related to DataSource[4] modification. | Table B13.9                                             |
| Clarification: DoNotGoToSD value encoding description is incorrect for SnpQuery and SnpStash*                                                        | Table B13.29                                            |
| Clarification: Comp can be used for WriteBack,                                                                                                       | Table B9.7                                              |

Continued on next page