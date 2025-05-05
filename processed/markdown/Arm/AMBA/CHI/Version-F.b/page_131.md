Table B2.8 Continued from previous page

| Request type      | CompAck required   | CompAck required   |
|-------------------|--------------------|--------------------|
|                   | RN-F               | RN-D, RN-I         |
| MakeInvalid       | N                  | N                  |
| WriteBack         | H                  | -                  |
| WriteClean        | H                  | -                  |
| WriteUnique       | O                  | O                  |
| WriteUniqueZero   | N                  | N                  |
| Evict             | N                  | -                  |
| WriteEvictFull    | H                  | -                  |
| WriteEvictOrEvict | H                  | -                  |
| WriteNoSnp        | O                  | O                  |
| WriteNoSnpDef     | N                  | N                  |
| WriteNoSnpZero    | N                  | N                  |
| Atomics           | N                  | N                  |
| StashOnce*        | N                  | N                  |

In a Combined Write transaction, the CompAck requirement is the same as the CompAck requirement for the type of Write in the Combined Write transaction.

### B2.6.4 Ordering semantics of RespSepData and DataSepResp

When a Requester receives the first DataSepResp, the Read transaction can be considered to be globally observed. This is because there is no action which can modify the read data received.

When a Requester receives a RespSepData response from Home, the relevent request has been ordered at Home. The Requester does not receive any snoops for transactions that are scheduled before the RespSepData response. Before sending RespSepData response to the Requester, the Home must ensure that no Snoop transactions are outstanding to that Requester to the same address. Receiving of RespSepData does not guarantee that Home has completed snooping of other agents in the system.

When the Requester gives a completion acknowledge, CompAck, response, this Requester is indicating to accept responsibility to hazard snoops for any transaction that is scheduled after the CompAck response. The following rules apply:

- For all transactions, except as described immediately below, the CompAck must be sent after the RespSepData response is received. It is permitted, but not required, to wait for the DataSepResp response before the CompAck is given.
- For ReadOnce and ReadNoSnp transactions with an ordering requirement, that is, Order field is set to 0b10 or 0b11 and ExpCompAck field is asserted, it is required that the CompAck is given only after both DataSepResp and RespSepData responses are received.

> **_NOTE:_** It is required that CompAck must not be given when only DataSepResp is received.