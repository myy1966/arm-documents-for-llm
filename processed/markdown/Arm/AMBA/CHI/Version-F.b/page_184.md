#### B4.2.1.1 Read request attribute values

This section discusses the attribute values for Read requests across node interfaces.

See Chapter C1 Message Field Mappings for complete list.

Table B4.1 lists permitted values for the key attributes in Read requests for Request Node to Home Node.

Table B4.1: Request Node to Home Node Read request permitted attribute values

| Request                                             | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                       | Order    | LikelyShared | ExpCompAck |
|-----------------------------------------------------|--------------|------|---------|---------------------------------------|----------|--------------|------------|
| ReadNoSnp                                           | <=64         | 0,1  | 0       | 0010                                  | 11       | 0            | 0,1        |
| ReadNoSnp                                           | <=64         | 0,1  | 0       | 0011                                  | 00,10,11 | 0            | 0,1        |
| ReadNoSnp                                           | <=64         | 0,1  | 0       | 0000 </br> 0001 </br> 0101 </br> 1101 | 00,10    | 0            | 0,1        |
| ReadOnce </br> ReadOnceCleanInvalid                 | <=64         | 0    | 1       | 0101                                  | 00,10    | 0            | 0,1        |
| ReadOnce </br> ReadOnceCleanInvalid                 | <=64         | 0    | 1       | 1101                                  | 00,10    | 0            | 0,1        |
| ReadOnceMakeInvalid                                 | <=64         | 0    | 1       | 0101                                  | 00,10    | 0            | 0,1        |
| ReadClean </br> ReadNotSharedDirty </br> ReadShared | 64           | 0,1  | 1       | 0101 </br> 1101                       | 00       | 0,1          | 1          |
| ReadUnique                                          | 64           | 0    | 1       | 0101                                  | 00       | 0            | 1          |
| ReadPreferUnique MakeReadUnique                     | 64           | 0,1  | 1       | 0101 </br> 1101                       | 00       | 0            | 1          |

Table B4.2 lists the permitted values for the key attributes in Read requests for HN-F to SN-F.