## C1.1 Request message field mappings

- C1.1.1 Read, Dataless and Miscellaneous
- C1.1.2 Write and Combined Write
- C1.1.3 Stash and Atomic

### C1.1.1 Read, Dataless and Miscellaneous

Table C1.2 and Table C1.3 show the Read, Dataless and Miscellaneous Request message field mappings. See Table C1.1 for the conventions used in the field mappings. For further information on field use see B13.10 Protocol flit fields.

Table C1.2: Read, Dataless and Miscellaneous Request message field mappings Part 1

| Request message       | QoS | TgtID | SrcID | TxnID | Opcode | AllowRetry | PCrdType RSVDC | RSVDC | TagOp | TraceTag | MPAM | PBHA | Addr | NSE | NS | Size | Order | LikelyShared | ExpCompAck |
|-----------------------|-----|-------|-------|-------|--------|------------|----------------|-------|-------|----------|------|------|------|-----|----|------|-------|--------------|------------|
| ReqLCrdReturn         | X   | X     | X     | 0     | Y      | X          | X              | X     | X     | X        | X    | X    | X    | X   | X  | X    | X     | X            | X          |
| PCrdReturn            | Y   | Y     | Y     | 0ᵃ    | Y      | 0ᵃ         | Y              | Y     | 0ᵃ    | Y        | 0ᵃ   | 0ᵃ   | 0ᵃ   | 0ᵃ  | 0ᵃ | 0ᵃ   | 0ᵃ    | 0ᵃ           | 0          |
| DVMOp                 | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0ᵃ    | Y        | 0ᵃ   | 0ᵃ   | M    | 0ᵃ  | 0ᵃ | 8B   | 0ᵃ    | 0ᵃ           | 0          |
| PrefetchTgt           | Y   | Y     | Y     | X     | Y      | 0          | X              | Y     | Y     | Y        | Y    | Y Y  | Y    |     | Y  | X    | X     | X            | 0ᵃ         |
| ReadNoSnp             | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | Y          |
| ReadNoSnpSep          | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | 0          |
| ReadOnce              | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | Y          |
| ReadOnceCleanInvalid  | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | Y          |
| ReadOnceMakeInvalid   | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | Y    | Y     | 0            | Y          |
| ReadClean             | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 1          |
| ReadNotSharedDirty    | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 1          |
| ReadShared            | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 1          |
| ReadUnique            | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 1          |
| ReadPreferUnique      | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 1          |
| MakeReadUnique        | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | Y            | 1          |
| CleanShared           | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0ᵃ    | 0            | 0          |
| CleanSharedPersist    | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0ᵃ    | 0            | 0          |
| CleanSharedPersistSep | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0ᵃ    | 0            | 0          |
| CleanInvalid          | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0ᵃ    | 0            | 0          |
| CleanInvalidPoPA      | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0ᵃ    | 0            | 0          |
| MakeInvalid           | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0ᵃ    | 0            | 0          |
| CleanUnique           | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | 0            | 1          |
| MakeUnique            | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | Y     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | 0            | 1          |
| Evict                 | Y   | Y     | Y     | Y     | Y      | Y          | Y              | Y     | 0     | Y        | Y    | Y    | Y    | Y   | Y  | 64B  | 0     | 0            | 0          |