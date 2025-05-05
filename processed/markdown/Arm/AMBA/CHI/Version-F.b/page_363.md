Table B9.13: Legal RespErr field values in Response packets for DVM transactions

| DVMtransaction | Associated Response packets </br> DBIDResp | Associated Response packets </br> Comp </br> OK | Associated Response packets </br> Comp </br> EXOK | Associated Response packets </br> Comp </br> DERR | Associated Response packets </br> Comp </br> NDERR | Associated Response packets </br> CompDBIDResp </br> OK | Associated Response packets </br> CompDBIDResp </br> EXOK | Associated Response packets </br> CompDBIDResp </br> DERR | Associated Response packets </br> CompDBIDResp </br> NDERR |
|----------------|--------------------------------------------|-------------------------------------------------|---------------------------------------------------|---------------------------------------------------|----------------------------------------------------|---------------------------------------------------------|-----------------------------------------------------------|-----------------------------------------------------------|------------------------------------------------------------|
| DVMOp          | OK                                         | Y                                               | N                                                 | Y                                                 | Y                                                  | Y                                                       | N                                                         | Y                                                         | Y                                                          |

Table B9.14 shows the DVM transaction Data packets legal RespErr field values.

Table B9.14: Legal RespErr field values in Data packets for DVM transactions

| DVMtransaction | Associated Response packets </br> NCBWrData </br> OK | Associated Response packets </br> NCBWrData </br> EXOK | Associated Response packets </br> NCBWrData </br> DERR | Associated Response packets </br> NCBWrData </br> NDERR |
|----------------|------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------|---------------------------------------------------------|
| DVMOp          | Y                                                    | N                                                      | Y                                                      | N                                                       |

##### B9.1.4.5.2 PrefetchTgt

A PrefetchTgt transaction request to a non-supporting address must be discarded.

> **_NOTE:_** The note content. A component is permitted, but not required, to record and report such an error.

#### B9.1.4.6 Cache Stashing transactions

If the specified Stash target does not support receiving Stash snoops, the Home must disregard the Stash hint and complete the transaction without Stashing. Examples of such Stash targets are RN-I, RN-D, legacy RN-F, or a Non-request node. In these circumstances, Home must not signal an error to the Requester. Such a wrongly specified Stash target can be attributed to a software-based error.

If the Home does not support Stash requests, the transaction must be completed in a protocol-compliant manner without signaling an error.

#### B9.1.4.7 Snoop transactions

A Snoop transaction response that includes data can indicate a DERR. A Snoop transaction response that includes data can mix OK and DERR responses for different packets within the transaction.

Data, in response to a Snoop request that is known to be corrupt, must have an appropriate Error indication where the error can be Poison or DERR.

A Snoop transaction response that does not include data can indicate an NDERR.

A Snoopee that responds with an NDERR:

- Must not include data with the response.