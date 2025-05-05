Table B4.15: HN-F to SN-F Write request permitted attribute values

| Request        | Size (bytes) | Excl | DoDWT | MemAttr A C D E                       | Order | LikelyShared | ExpCompAck |
|----------------|--------------|------|-------|---------------------------------------|-------|--------------|------------|
| WriteNoSnpFull | 64           | 0,1  | 0,1   | 0000 </br> 0001 </br> 0101 </br> 1101 | 00    | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpPtl  | <=64         | 0,1  | 0,1   | 0000 </br> 0001 </br> 0101 </br> 1101 | 00    | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpZero | 64           | 0    | 0 ᵃ   | 0000 </br> 0001 </br> 0101 </br> 1101 | 00    | 0 ᵃ          | 0 ᵃ        |

- ᵃ The field is inapplicable and must be set to 0

Table B4.16: HN-I to SN-I Write request permitted attribute values

| Request        | Size (bytes) | Excl | DoDWT | MemAttr A C D E                       | Order    | LikelyShared | ExpCompAck |
|----------------|--------------|------|-------|---------------------------------------|----------|--------------|------------|
| WriteNoSnpFull | 64           | 0,1  | 0,1   | 0010                                  | 11       | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpFull | 64           | 0,1  | 0,1   | 0011                                  | 00,10,11 | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpFull | 64           | 0,1  | 0,1   | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0 ᵃ          | 0 ᵃ        |

- ᵃ The field is inapplicable and must be set to 0

Continued on next page