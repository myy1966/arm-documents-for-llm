### C1.1.3 Stash and Atomic

Table C1.6 and Table C1.7 show the Stash and Atomic Request message field mappings. See Table C1.1 for the conventions used in the field mappings. For further information on field use see B13.10 Protocol flit fields.

Table C1.6: Stash and Atomic Request message field mappings part 1

| Request message    | QoS | TgtID | SrcID | TxnID | Opcode | AllowRetry | PCrdType | RSVDC | TagOp | TraceTag | MPAM | PBHA | Addr | NSE | NS | Size | Order | LikelyShared | ExpCompAck |
|--------------------|-----|-------|-------|-------|--------|------------|----------|-------|-------|----------|------|------|------|-----|----|------|-------|--------------|------------|
| StashOnceUnique    | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 0          |
| StashOnceSepUnique | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 0          |
| StashOnceShared    | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 0          |
| StashOnceSepShared | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 0          |
| AtomicLoad         | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | 0          |
| AtomicStore        | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | 0          |
| AtomicCompare      | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | 0          |
| AtomicSwap         | Y   | Y     | Y     | Y     | Y      | Y          | Y        | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | 0          |

Table C1.7: Stash and Atomic Request message field mappings part 2

|                    | MemAttr  | MemAttr   | MemAttr | MemAttr | CF      | CF    | CF   | CF      | CF  | CF   | CF         | CF           | CF       | CF        | CF       | CF         | CF            | CF     | CF   | CF          | CF             | CF        |
|--------------------|----------|-----------|---------|---------|---------|-------|------|---------|-----|------|------------|--------------|----------|-----------|----------|------------|---------------|--------|------|-------------|----------------|-----------|
| Request message    | Allocate | Cacheable | Device  | EWA     | SnpAttr | DoDWT | Excl | SnoopMe | CAH | LPID | TagGroupID | StashGroupID | PGroupID | ReturnNID | StashNID | SLCRepHint | StashNIDValid | Endian | Deep | ReturnTxnID | StashLPIDValid | StashLPID |
| StashOnceUnique    | Y        | 1         | 0       | 1       | 1       | -     | 0    | -       | -   | Y    | -          | -            | -        | -         | Y        | Y          | Y             | -      | -    | -           | Y              | Y         |
| StashOnceSepUnique | Y        | 1         | 0       | 1       | 1       | -     | 0    | -       | -   | -    | -          | Y            | -        | -         | Y        | Y          | Y             | -      | -    | -           | Y              | Y         |
| StashOnceShared    | Y        | 1         | 0       | 1       | 1       | -     | 0    | -       | -   | Y    | -          | -            | -        | -         | Y        | Y          | Y             | -      | -    | -           | Y              | Y         |
| StashOnceSepShared | Y        | 1         | 0       | 1       | 1       | -     | 0    | -       | -   | -    | -          | Y            | -        | -         | Y        | Y          | Y             | -      | -    | -           | Y              | Y         |
| AtomicLoad         | Y        | Y         | Y       | Y       | Y       | -     | -    | Y       | -   | Y    | Y          | -            | -        | Y         | -        | -          | -             | Y      | -    | Y           | -              | -         |
| AtomicStore        | Y        | Y         | Y       | Y       | Y       | -     | -    | Y       | -   | Y    | Y          | -            | -        | Y         | -        | -          | -             | Y      | -    | X           | -              | -         |
| AtomicCompare      | Y        | Y         | Y       | Y       | Y       | -     | -    | Y       | -   | Y    | Y          | -            | -        | Y         | -        | -          | -             | Y      | -    | Y           | -              | -         |
| AtomicSwap         | Y        | Y         | Y       | Y       | Y       | -     | -    | Y       | -   | Y    | Y          | -            | -        | Y         | -        | -          | -             | Y      | -    | Y           | -              | -         |