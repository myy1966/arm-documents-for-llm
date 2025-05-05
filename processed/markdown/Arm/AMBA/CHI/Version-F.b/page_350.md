Table B8.19: Fixed field values for a Virtual Instruction Cache Invalidatee message

| Field    | Value | Status                               |
|----------|-------|--------------------------------------|
| DVMType  | 0b011 | Virtual Instruction Cache Invalidate |
| Part Num | -     | See Table B8.10                      |
| Stage    | 0b00  | Reserved, set to 0                   |
| Leaf     | 0b0   | Reserved, set to 0                   |

Table B8.20 shows the operations supported by VICI.

Table B8.20: Virtual Istruction Cache Invalidate operations

| Operation                                                   | Arm  | Exception | Security | VMIDV | ASIDV | AddV |
|-------------------------------------------------------------|------|-----------|----------|-------|-------|------|
| Hypervisor and all Guest OS VICI all, Secure and Non-secure | v7   | 0b00      | 0b00     | 0b0   | 0b0   | 0b0  |
| Hypervisor and all Guest OS VICI all, Non-secure only       | v7   | 0b00      | 0b11     | 0b0   | 0b0   | 0b0  |
| All Guest OS VICI by ASID and VA, Secure only               | v7   | 0b10      | 0b10     | 0b0   | 0b1   | 0b1  |
| All Guest OS VICI by VMID, Secure only                      | v8.4 | 0b10      | 0b10     | 0b1   | 0b0   | 0b0  |
| All Guest OS VICI by ASID, VA and VMID, Secure only         | v8.4 | 0b10      | 0b10     | 0b1   | 0b1   | 0b1  |
| All Guest OS VICI by VMID, Non-secure only                  | v7   | 0b10      | 0b11     | 0b1   | 0b0   | 0b0  |
| All Guest OS VICI by ASID, VA and VMID, Non-secure only     | v7   | 0b10      | 0b11     | 0b1   | 0b1   | 0b1  |
| Hypervisor VICI by VA, Non-secure only                      | v7   | 0b11      | 0b11     | 0b0   | 0b0   | 0b1  |
| Hypervisor VICI by ASID and VA, Non-secure only             | v8.1 | 0b11      | 0b11     | 0b0   | 0b1   | 0b1  |

### B8.4.6 Synchronization

This section describes the DVMSync operation.

A Synchronization (Sync) message is used when the Requester needs to know when all previous invalidations are complete.

The fixed field values for a Sync message are shown in Table B8.21.

Table B8.21: Sync operation fixed values

| Field    | Value | Status                  |
|----------|-------|-------------------------|
| DVMType  | 0b100 | Synchronization message |
| Part Num | -     | See Table B8.10         |
| AddrV    | 0b0   | No address information  |
| VMIDV    | 0b0   | No VMID information     |

Continued on next page