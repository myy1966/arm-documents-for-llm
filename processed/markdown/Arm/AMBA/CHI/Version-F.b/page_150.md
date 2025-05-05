### B2.7.8 CopyAtHome attribute

CopyAtHome, CAH, is a cache line attribute that can be used by Home to optimize away redundant data transfers. It is useful in topologies where system caches are neither fully-inclusive or fully-exclusive, but which adapt their inclusion policy depending on the behavior of the system.

In CompData and DataSepResp response to the Requester, the CAH value indicates if the Home keeps a copy of the line. The CAH value is cached with the line at the Requester. If the line is updated locally, the cached CAH attribute must be reset.

When the Requester performs a CopyBack Write or Combined CopyBack Write for the line, the CAH value is sent along with the request. The Home can use the CAH value in the request to determine if it should check for a local copy of the line. If Home still retains a copy of the line, the CopyBack Write transaction is requested to complete without a CopyBackWriteData transfer.

#### B2.7.8.1 CAH usage at Home

In CompData or DataSepResp responses from Home, the CAH attribute is set to:

**1** If the Home indicates a copy of the line is being kept. If the Home has provided a Requester with a Unique copy of the line, the copy at the Home is a hidden copy and is not observable to any agents in the system. If the Hidden copy is Clean, Home is permitted to remove the copy of the cache line at any time, except for during the window where a Comp has been issued and the associated CompAck is still outstanding. Home is not permitted to remove the hidden copy of the line if the line is Dirty.

**0** If the Home intends to not keep a copy of the line nor supports the optimized CopyBack Write flow.

When the Home receives a later CopyBack Write request, it can inspect the CAH attribute to establish the transaction flow variation for use to complete the transaction. Table B2.14 shows the CAH attribute usage at Home for CopyBack Write transactions.

Table B2.14: CAH usage at Home for CopyBack Write transactions

| Request CAH value | CopyBack Write transaction               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|-------------------|------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                 | WriteBack, WriteClean, or WriteEvictFull | The Home is permitted to do one of the following: </br> • Respond with CompDBIDResp to request the write data for the transaction. </br> • Check if Home still has a copy of the line: </br> **If Home has a copy of the line**: The Home is expected, but not required, to respond with Comp to request that the transaction is completed without a data transfer. If the Home does not send Comp, it must send CompDBIDResp, to request the write data for the transaction. </br> **If Home does not have a copy of the line** : The Home must respond with CompDBIDResp to request the write data for the transaction. |

Continued on next page