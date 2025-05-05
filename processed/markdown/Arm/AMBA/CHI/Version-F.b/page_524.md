## C2.3 Response communicating nodes

Table C2.3 shows the Response communicating nodes.

Table C2.3: Response communicating nodes

<!-- MERGE table -->

| Response   |               | From                | To                          |
|------------|---------------|---------------------|-----------------------------|
| Upstream   | RetryAck      | ICN(HN-F, HN-I, MN) | RN-F, RN-D, RN-I            |
|            | PCrdGrant     | SN-F                | ICN(HN-F)                   |
|            | Comp          | SN-I                | ICN(HN-I)                   |
|            | CompDBIDResp  |                     |                             |
|            | CompCMO       | ICN(HN-F, HN-I)     | RN-F, RN-D, RN-I            |
|            | ReadReceipt   | SN-F                | ICN(HN-F)                   |
|            |               | SN-I                | ICN(HN-I)                   |
|            | RespSepData   | ICN(HN-F, HN-I)     | RN-F, RN-D, RN-I            |
|            | DBIDResp      | ICN(HN-F, HN-I, MN) | RN-F, RN-D, RN-I            |
|            |               | SN-F                | ICN(HN-F), RN-F, RN-D, RN-I |
|            |               | SN-I                | ICN(HN-I), RN-F, RN-D, RN-I |
|            | DBIDRespOrd   | ICN(HN-F, HN-I)     | RN-F, RN-D, RN-I            |
|            | StashDone     | ICN(HN-F)           | RN-F, RN-D, RN-I            |
|            | CompStashDone |                     |                             |
|            | TagMatch      | ICN(HN-F)           | RN-F, RN-D, RN-I            |
|            |               | SN-F                | ICN(HN-F), RN-F, RN-D, RN-I |
|            | Persist       | ICN(HN-F, HN-I)     | RN-F, RN-D, RN-I            |
|            |               | SN-F                | ICN(HN-F), RN-F, RN-D, RN-I |
|            |               | SN-I                | ICN(HN-I), RN-F, RN-D, RN-I |
|            | CompPersist   | ICN(HN-F, HN-I)     | RN-F, RN-D, RN-I            |
|            |               | SN-F                | ICN(HN-F)                   |
|            |               | SN-I                | ICN(HN-I)                   |
| Downstream | CompAck       | RN-F, RN-D, RN-I    | ICN(HN-F, HN-I)             |
|            | SnpResp       | RN-F                | ICN(HN-F)                   |
|            |               | RN-F, RN-D          | ICN(MN)                     |
|            | SnpRespFwded  | RN-F                | ICN(HN-F)                   |