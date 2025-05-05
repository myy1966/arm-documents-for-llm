## C1.3 Snoop Request message field mappings

Table C1.9shows the snoop request message field mappings. See Table C1.1 for the conventions used in the field mappings. For further information on field use see B13.10 Protocol flit fields.

Table C1.9: Snoop Request message field mappings

|                       |     |       |       |        |      |     |     |             |          |          |      | CF     | CF   | CF       | CF             | CF        | CF      |
|-----------------------|-----|-------|-------|--------|------|-----|-----|-------------|----------|----------|------|--------|------|----------|----------------|-----------|---------|
| Snoop Request message | QoS | SrcID | TxnID | Opcode | Addr | NSE | NS  | DoNotGoToSD | RetToSrc | TraceTag | MPAM | FwdNID | PBHA | FwdTxnID | StashLPIDValid | StashLPID | VMIDExt |
| SnpLCrdReturn         | X   | X     | 0     | Y      | X    | X   | X   | X           | X        | X        | X    | X      | X    | X        | X              | X         | X       |
| SnpShared             | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpClean              | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpOnce               | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpNotSharedDirty     | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpUnique             | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | Y        | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpPreferUnique       | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpCleanShared        | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpCleanInvalid       | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpMakeInvalid        | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpSharedFwd          | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | Y      | -    | Y        | -              | -         | -       |
| SnpCleanFwd           | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | Y      | -    | Y        | -              | -         | -       |
| SnpOnceFwd            | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | 0ᵃ       | Y        | D    | Y      | -    | Y        | -              | -         | -       |
| SnpNotSharedDirtyFwd  | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | Y      | -    | Y        | -              | -         | -       |
| SnpUniqueFwd          | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | D    | Y      | -    | Y        | -              | -         | -       |
| SnpPreferUniqueFwd    | Y   | Y     | Y     | Y      | Y    | Y   | Y   | Y           | Y        | Y        | D    | Y      | -    | Y        | -              | -         | -       |
| SnpUniqueStash        | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | Y    | -      | Y    | -        | Y              | Y         | -       |
| SnpMakeInvalidStash   | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | Y    | -      | Y    | -        | Y              | Y         | -       |
| SnpStashUnique        | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | Y    | -      | Y    | -        | Y              | Y         | -       |
| SnpStashShared        | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 1           | 0ᵃ       | Y        | Y    | -      | Y    | -        | Y              | Y         | -       |
| SnpQuery              | Y   | Y     | Y     | Y      | Y    | Y   | Y   | 0ᵃ          | 0ᵃ       | Y        | D    | 0ᵃ     | 0ᵃ   | 0ᵃ       | 0ᵃ             | 0ᵃ        | 0ᵃ      |
| SnpDVMOp              | Y   | Y     | Y     | Y      | M    | 0ᵃ  | 0ᵃ  | 0ᵃ          | 0ᵃ       | Y        | 0ᵃ   | M      | M    | -        | -              | -         | Y       |