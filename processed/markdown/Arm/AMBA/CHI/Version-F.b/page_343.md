Table B8.10 Continued from previous page

| X in </br> REQ.Addr[x] </br> DAT.Data[x] | Num bits | DVMOp REQ                    | DVMOp DAT                      |
|------------------------------------------|----------|------------------------------|--------------------------------|
| 7                                        | 1        | Security[0]                  | IS[1] </br> TTL[1] </br> PA[9] |
| 8                                        | 1        | Security[1]                  | IS[2] </br> TG[0] </br> PA[10] |
| 9                                        | 1        | Exception[0]                 | IS[3] </br> TG[1] </br> PA[11] |
| 10                                       | 1        | Exception[1]                 | VA[12] </br> PA[12]            |
| 13:11                                    | 3        | DVMType[2:0]                 | VA[15:13] </br> PA[15:13]      |
| 21:14                                    | 8        | VMID[7:0] </br> VI[27:20]    | VA[23:16] </br> PA[23:16]      |
| 37:22                                    | 16       | ASID[15:0] </br> VI[19:12] ᵇ | VA[39:24] </br> PA[39:24]      |
| 39:38                                    | 2        | Stage                        | VA[41:40] </br> PA[6]          |
| 40                                       | 1        | Leaf                         | VA[42] </br> PA[42]            |
| 41                                       | 1        | Range ᶜ                      | VA[43] </br> PA[43]            |
| 42                                       | 1        | Num[4] ᵃ                     | VA[44] </br> PA[44]            |
| 43                                       | 1        | -                            | VA[45] </br> PA[45]            |
| 44                                       | 1        | -                            | VA[46] </br> PA[46]            |
| 45                                       | 1        | -                            | VA[47] </br> PA[47]            |
| 48:46                                    | 3        | -                            | VA[50:48] </br> PA[50:48]      |
| 49                                       | 1        | -                            | VA[51] </br> PA[51]            |
| 50                                       | 1        | -                            | VA[52]                         |
| 55:51                                    | 5        | -                            | -                              |
| 63:56                                    | 8        | -                            | VMID[15:8] ᵈ                   |

| X in </br> SNP.Addr[x] | Num bits | SnpDVMOp Request Part 1 | SnpDVMOp Request Part 2        |
|------------------------|----------|-------------------------|--------------------------------|
| 4                      | 1        | Security[0]             | IS[1] </br> TTL[1] </br> PA[9] |
| 5                      | 1        | Security[1]             | IS[2] </br> TG[0] </br> PA[10] |
| 6                      | 1        | Exception[0]            | IS[3] </br> TG[1] </br> PA[11] |
| 7                      | 1        | Exception[1]            | VA[12] </br> PA[12]            |
| 10:8                   | 3        | DVMType[2:0]            | VA[15:13] </br> PA[15:13]      |
| 18:11                  | 8        | VMID[7:0]               | VA[23:16] </br> PA[23:16]      |
| 34:19                  | 16       | ASID[15:0]              | VA[39:24] </br> PA[39:24]      |
| 36:35                  | 2        | Stage                   | VA[41:40] </br> PA[41:40]      |
| 37                     | 1        | Leaf                    | VA[42] </br> PA[42]            |
| 38                     | 1        | VA[46]                  | VA[43] </br> PA[43]            |
| 39                     | 1        | VA[47]                  | VA[44] </br> PA[44]            |
| 40                     | 1        | VA[48]                  | VA[45] </br> PA[45]            |
| 41                     | 1        | VA[50]                  | VA[49] </br> PA[46]            |
| 42                     | 1        | VA[52]                  | VA[51] </br> PA[47]            |
| 45:43                  | 3        | -                       | PA[50:48]                      |
| 46                     | 1        | -                       | PA[51]                         |
| 47                     | 1        | -                       | -                              |
| 48                     | 1        | -                       | -                              |

- ᵃ For Part 2 of a SnpDVMOp request, Num[4:0] from the corresponding DVMOp request is carried on the FwdNID field of the Snoop flit alongside the Addr field. See Table B8.14.
- ᵇ When used as Virtual Index VA (VI VA), REQ.Addr[37:30], DAT.Data[37:30], and SNP.Addr[34:27] can take any value.
- ᶜ For Part 1 of a SnpDVMOp request, Range from the corresponding DVMOp request is carried on the FwdNID field of the Snoop flit alongside the Addr field. See Table B8.14.
- ᵈ For Part 1 of a SnpDVMOp request, VMID[15:8] from the corresponding DVMOp request is carried on the VMIDExt field of the Snoop flit alongside the Addr field. See Table B13.8