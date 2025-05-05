Table B4.2: HN-F to SN-F Read request permitted attribute values

| Request      | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                       | Order | LikelyShared | ExpCompAck |
|--------------|--------------|------|---------|---------------------------------------|-------|--------------|------------|
| ReadNoSnp    | <=64         | 0,1  | 0       | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,01 | 0            | 0          |
| ReadNoSnpSep | <=64         | 0    | 0       | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,01 | 0            | 0          |

Table B4.3 lists the permitted values for the key attributes in Read requests for HN-I to SN-I.

Table B4.3: Request Node to Home Node Read request permitted attribute values

| Request      | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                       | Order       | LikelyShared | ExpCompAck |
|--------------|--------------|------|---------|---------------------------------------|-------------|--------------|------------|
| ReadNoSnp    | <=64         | 0,1  | 0       | 0010                                  | 11          | 0            | 0          |
| ReadNoSnp    | <=64         | 0,1  | 0       | 0011                                  | 00,01,10,11 | 0            | 0          |
| ReadNoSnp    | <=64         | 0,1  | 0       | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,01,10    | 0            | 0          |
| ReadNoSnpSep | <=64         | 0    | 0       | 0010                                  | 11          | 0            | 0          |
| ReadNoSnpSep | <=64         | 0    | 0       | 0011                                  | 00,01,10,11 | 0            | 0          |
| ReadNoSnpSep | <=64         | 0    | 0       | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,01,10    | 0            | 0          |
