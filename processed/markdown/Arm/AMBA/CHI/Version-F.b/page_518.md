## C1.4 Data message field mappings

Table C1.10ᵃ md Table C1.11 show the Data message field mappings. See Table C1.1 for the conventions used in the field mappings. For further information on field use see B13.10 Protocol flit fields.

Table C1.10: Data message field mappings part 1

| Data message                | QoS | TgtID | SrcID | TxnID | Opcode | RespErr | Resp | CBusy | DBID | CCID | DataID | RSVDC | BE | Data | TraceTag | CAH | DataCheck | Poison | TagOp | Tag | TU |
|-----------------------------|-----|-------|-------|-------|--------|---------|------|-------|------|------|--------|-------|----|------|----------|-----|-----------|--------|-------|-----|----|
| DatLCrdReturn               | X   | X     | X     | 0     | Y      | X       | X    | X     | X    | X X  | X      | X     | X  | X    | X        | X   | X         | X      | X     | X   | X  |
| SnpRespData                 | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | Y    | Y    | Y Y    | Y     | Y  | Y    | Y        | Y   | Y         | Y      | Y     | Y   | Y  |
| SnpRespDataFwded            | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | X    | Y    | Y      | Y     | Y  | Y    | Y        | Y   | Y         | Y      | Y     | Y   | Y  |
| CopyBackWriteData           | Y   | Y     | Y     | Y     | Y      | Y       | Y    | 0ᵃ    | X    | Y    | Y      | Y     | Y  | Y    | Y        | 0ᵃ  | Y         | Y      | Y     | Y   | Y  |
| NonCopyBackWriteData        | Y   | Y     | Y     | Y     | Y      | Y       | 0    | 0ᵃ    | X    | Y    | Y      | Y     | Y  | Y    | Y        | 0ᵃ  | Y         | Y      | Y     | Y   | Y  |
| NonCopyBackWriteDataCompAck | Y   | Y     | Y     | Y     | Y      | Y       | 0    | 0ᵃ    | X    | Y    | Y      | Y     | Y  | Y    | Y        | 0ᵃ  | Y         | Y      | Y     | Y   | Y  |
| CompData                    | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | Y    | Y    | Y      | Y     | X  | Y    | Y        | Y   | Y         | Y      | Y     | Y   | Y  |
| DataSepResp                 | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | Y    | Y    | Y      | Y     | X  | Y    | Y        | Y   | Y         | Y      | Y     | Y   | Y  |
| SnpRespDataPtl              | Y   | Y     | Y     | Y     | Y      | Y       | Y    | Y     | Y    | Y    | Y      | Y     | Y  | Y    | Y        | 0   | Y         | Y      | Y     | Y   | Y  |
| WriteDataCancel             | Y   | Y     | Y     | Y     | Y      | Y       | 0    | 0ᵃ    | X    | Y    | Y      | Y     | 0  | 0    | Y        | 0ᵃ  | Y         | Y      | Y     | Y   | Y  |

Table C1.11: Data message field mappings part 2

|                             | CF      | CF   | CF       | CF       | CF         |
|-----------------------------|---------|------|----------|----------|------------|
| Data message                | HomeNID | PBHA | FwdState | DataPull | DataSource |
| DatLCrdReturn               | X       | X    | X        | X        | X          |
| SnpRespData                 | -       | Y    | -        | Y        | Y          |
| SnpRespDataFwded            | -       | Y    | Y        | -        | -          |
| CopyBackWriteData           | 0ᵃ      | 0ᵃ   | 0ᵃ       | 0ᵃ       | 0ᵃ         |
| NonCopyBackWriteData        | 0ᵃ      | 0ᵃ   | 0ᵃ       | 0ᵃ       | 0ᵃ         |
| NonCopyBackWriteDataCompAck | 0ᵃ      | 0ᵃ   | 0ᵃ       | 0ᵃ       | 0ᵃ         |
| CompData                    | Y       | -    | -        | -        | Y          |
| DataSepResp                 | Y       | -    | -        | -        | Y          |
| SnpRespDataPtl              | -       | Y    | -        | Y        | Y          |
| WriteDataCancel             | 0ᵃ      | 0ᵃ   | 0ᵃ       | 0ᵃ       | 0ᵃ         |