## C1.2 Response message field mappings

Table C1.8 shows the Response message field mappings. See Table C1.1 for the conventions used in the field mappings. For further information on field use see B13.10 Protocol flit fields.

Table C1.8: Response message field mappings

|                  |     |       |       |       |        |         |      |       |       |          |          | CF   | CF         | CF           | CF       | CF       | CF       |
|------------------|-----|-------|-------|-------|--------|---------|------|-------|-------|----------|----------|------|------------|--------------|----------|----------|----------|
| Response message | QoS | TgtID | SrcID | TxnID | Opcode | RespErr | Resp | CBusy | TagOp | TraceTag | PCrdType | DBID | TagGroupID | StashGroupID | PGroupID | FwdState | DataPull |
| RspLCrdReturn    | X   | X     | X     | 0     | Y      | X       | X    | X     | X     | X        | X        | X    | X          | X            | X        | X        | X        |
| SnpResp          | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | 0ᵃ    | Y        | 0ᵃ       | Y    | -          | -            | -        | -        | Y        |
| SnpRespFwded     | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | 0ᵃ    | Y        | 0ᵃ       | X    | -          | -            | -        | Y        | -        |
| CompAck          | Y   | Y     | Y     | Y     | Y      | 0       | Y    | 0ᵃ    | 0ᵃ    | Y        | 0ᵃ       | X    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| RetryAck         | Y   | Y     | Y     | Y     | Y      | 0       | 0ᵃ   | Y     | 0ᵃ    | Y        | Y        | X    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| Comp             | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | Y     | Y        | 0ᵃ       | Y    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| CompCMO          | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | 0ᵃ    | Y        | 0ᵃ       | X    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| Persist          | Y   | Y     | Y     | 0ᵃ    | Y      | Y       | 0ᵃ   | Y     | 0ᵃ    | X        | 0ᵃ       | -    | -          | -            | Y        | 0ᵃ       | 0ᵃ       |
| CompPersist      | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | 0ᵃ    | Y        | 0ᵃ       | -    | -          | -            | Y        | 0ᵃ       | 0ᵃ       |
| StashDone        | Y   | Y     | Y     | 0ᵃ    | Y      | Y       | 0ᵃ   | Y     | 0ᵃ    | X        | 0ᵃ       | -    | -          | Y            | -        | 0ᵃ       | 0ᵃ       |
| CompStashDone    | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | 0ᵃ    | Y        | 0ᵃ       | -    | -          | Y            | -        | 0ᵃ       | 0ᵃ       |
| RespSepData      | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | 0ᵃ    | Y        | 0ᵃ       | Y    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| CompDBIDResp     | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | 0ᵃ    | Y        | 0ᵃ       | Y    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| DBIDResp         | Y   | Y     | Y     | Y     | Y      | 0       | 0ᵃ   | Y     | 0ᵃ    | Y        | 0ᵃ       | Y    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| DBIDRespOrd      | Y   | Y     | Y     | Y     | Y      | 0       | 0ᵃ   | Y     | 0ᵃ    | Y        | 0ᵃ       | Y    | -          | -            | -        | 0ᵃ       | 0ᵃ       |
| TagMatch         | Y   | Y     | Y     | 0ᵃ    | Y      | Y       | Y    | Y     | 0ᵃ    | X        | 0ᵃ       | -    | Y          | -            | -        | 0ᵃ       | 0ᵃ       |
| PCrdGrant        | Y   | Y     | Y     | 0ᵃ    | Y      | 0       | 0ᵃ   | Y     | 0ᵃ    | Y        | Y        | 0ᵃ   | 0ᵃ         | 0ᵃ           | 0ᵃ       | 0ᵃ       | 0ᵃ       |
| ReadReceipt      | Y   | Y     | Y     | Y     | Y      | 0       | 0ᵃ   | Y     | 0ᵃ    | Y        | 0ᵃ       | X    | -          | -            | -        | 0ᵃ       | 0ᵃ       |