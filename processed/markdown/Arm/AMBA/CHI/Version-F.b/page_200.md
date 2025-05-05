Table B4.16 Continued from previous page

| Request        | Size (bytes) | Excl | DoDWT | MemAttr A C D E                       | Order    | LikelyShared | ExpCompAck |
|----------------|--------------|------|-------|---------------------------------------|----------|--------------|------------|
| WriteNoSnpPtl  | <=64         | 0,1  | 0,1   | 0010                                  | 11       | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpPtl  | <=64         | 0,1  | 0,1   | 0011                                  | 00,10,11 | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpPtl  | <=64         | 0,1  | 0,1   | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpDef  | 64           | 0    | 0,1   | 0010                                  | 11       | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpDef  | 64           | 0    | 0,1   | 0011                                  | 00,10,11 | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpDef  | 64           | 0    | 0,1   | 0000 </br> 0001                       | 00,10    | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpZero | 64           | 0    | 0 ᵃ   | 0010                                  | 11       | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpZero | 64           | 0    | 0 ᵃ   | 0011                                  | 00,10,11 | 0 ᵃ          | 0 ᵃ        |
| WriteNoSnpZero | 64           | 0    | 0 ᵃ   | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0 ᵃ          | 0 ᵃ        |

- ᵃ The field is inapplicable and must be set to 0

#### B4.2.3.4 Initial cache state at the Requester

Table B4.17 lists the permitted Requester cache states when a request is sent. The following key is used:

- Y Yes, permitted
- \-Not permitted

Table B4.17: Permitted Requester cache state at the sending of a Write request

| Request        | Initial state </br> UD | Initial state </br> UC | Initial state </br> SD | Initial state </br> SC | Initial state </br> I | Initial state </br> UDP | Initial state </br> UCE |
|----------------|------------------------|------------------------|------------------------|------------------------|-----------------------|-------------------------|-------------------------|
| WriteNoSnpPtl  | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteNoSnpFull | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteNoSnpDef  | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteNoSnpZero | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |

Continued on next page