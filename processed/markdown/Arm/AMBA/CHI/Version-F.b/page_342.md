***DVM* domain**

The SnpAttr bit in a DVM request is used to differentiate between Inner and Outer domain.

Table B8.9 shows the SnpAttr value encoding in DVM transactions.

Table B8.9: SnpAttr value encoding in DVM transactions

| SnpAttr | Domain value |
|---------|--------------|
| 0       | Inner domain |
| 1       | Outer domain |

Two additional optional interface broadcast pins are defined, **BROADCASTTLBIINNER** (BTI) and **BROARDCASTTLBIOUTER** (BTO). They determine broadcasting of TLBI operations in the interconnect. See B16.2 Optional interface broadcast signals.

### B8.4.2 DVM message packing

Table B8.10 shows the distribution of the payload in the DVMOp request from the Request Node, using 8-byte write semantics, and the distribution of the payload in the SnpDVMOp requests from the Miscellaneous Node.

In the DVMOp, the combination of the address field in the request and the 8-byte write data transports the complete payload. REQ.Addr[3] is not used in the request and must be set to 0.

In the two SnpDVMOp requests the combination of the two address fields transports the complete payload. SNP.Addr[0] is used in a SnpDVMOp request to indicate which part of the payload is being transported.

The valid combinations of Maximum PA (MPA) and Maximum VA (MVA) address bits are:

- MPA = 44 : MVA = 49
- MPA = 45 : MVA = 51
- MPA = 46 to 52 : MVA = 53

See B8.4.3.1 TLB Invalidate by Range and B8.4.3.2 Level Hint in TLBI operations.

Table B8.10: Security field encodings for each DVMType

| X </br> in REQ.Addr[x] </br> DAT.Data[x] | Num bits | DVMOp REQ          | DVMOp DAT                        |
|------------------------------------------|----------|--------------------|----------------------------------|
| 2:0                                      | 3        | -                  | Num[2:0] ᵃ                       |
| 3                                        | 1        | 0                  | Num[3] ᵃ                         |
| 4                                        | 1        | AddrV              | Scale[0] </br> PA[6] </br> VA[6] |
| 5                                        | 1        | VMIDV </br> VIV[0] | Scale[1] </br> PA[7] </br> VA[7] |
| 6                                        | 1        | ASIDV </br> VIV[1] | IS[0] </br> TTL[0] </br> PA[8]   |

| X in SNP.Addr[x] | Num bits | SnpDVMOp Request Part 1 | SnpDVMOp Request Part 2          |
|------------------|----------|-------------------------|----------------------------------|
| 0                | 1        | 0                       | 1                                |
| 1                | 1        | AddrV                   | Scale[0] </br> PA[6] </br> VA[6] |
| 2                | 1        | VMIDV </br> VIV[0]      | Scale[1] </br> PA[7] </br> VA[7] |
| 3                | 1        | ASIDV </br> VIV[1]      | IS[0] </br> TTL[0] </br> PA[8]   |

Continued on next page
