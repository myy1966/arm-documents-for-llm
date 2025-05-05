### B8.4.4 Branch Predictor Invalidate

This section describes the Branch Predictor Invalidate (BPI) operations.

The BPI message is used to invalidate virtual addresses from branch predictors.

The fixed field values for a BPI message are shown in Table B8.15.

Table B8.15: Fixed field values for a Branch Predictor Invalidate message

| Field        | Value  | Status                                 |
|--------------|--------|----------------------------------------|
| DVMType      | 0b001  | Branch Predictor Invalidate            |
| Part Num     | -      | See Table B8.10                        |
| VMIDV        | 0b0    | VMID field not valid                   |
| ASIDV        | 0b0    | ASID field not valid                   |
| Security     | 0b00   | Applies to both Secure and Non-secure  |
| Exception    | 0b00   | Applies to all Guest OS and Hypervisor |
| VMID VMIDExt | 0xXX   | VMID not specified                     |
| ASID         | 0xXXXX | ASID not specified                     |
| Stage        | 0b00   | Reserved, set to 0                     |
| Leaf         | 0b0    | Reserved, set to 0                     |

> **_NOTE:_** The use of BPI with a 16-bit ASID is not supported.

Table B8.16 shows the operations supported by BPI.

Table B8.16: Branch Predictor Invalidate operations

| Operation                         | Arm | AddrV |
|-----------------------------------|-----|-------|
| Branch Predictor Invalidate all   | v7  | 0b0   |
| Branch Predictor Invalidate by VA | v7  | 0b1   |

### B8.4.5 Instruction Cache Invalidate

Instruction caches can use either a PA or a V A to tag the data they contain. A system could contain a mixture of both forms of cache.

The DVM protocol includes instruction cache invalidation operations that use Physical Addresses and operations that use Virtual Addresses.

A component that receives DVM messages must support both forms of message, independent of the style of instruction cache implemented. In an instance where a message is received in a format that is not native to the cache type, over-invalidation might be required.