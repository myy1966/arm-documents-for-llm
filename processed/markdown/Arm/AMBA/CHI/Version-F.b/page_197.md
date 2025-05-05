**WriteEvictOrEvict**

WriteBack of Clean data to the next-level cache. This request type is merging of WriteEvictFull and Evict into one request. The Home Node is allowed to determine if data is sent.

- Data might not be sent if the Completer does not accept data.
- If data is sent, then the Data size is a cache line length.
- Table B4.13 indicates the initial state of the cache line when the request is sent:

Table B4.13: LikelyShared value states

|   LikelyShared | Initial state   |
|----------------|-----------------|
|              0 | UC              |
|              1 | SC              |

#### B4.2.3.3 Write request attribute values

This section discusses the attribute values for Write requests across node interfaces.

Table B4.14 lists the values permitted for key attributes in Write requests from Request Node to Home Node.

Table B4.14: Request Node to Home Node Write request attribute values

| Request        | Size (bytes) | Excl | SnpAttr | MemAttr A C D E                       | Order | LikelyShared | ExpCompAck |
|----------------|--------------|------|---------|---------------------------------------|-------|--------------|------------|
| WriteNoSnpFull | 64           | 0,1  | 0       | 0010                                  | 11    | 0            | 0          |
| WriteNoSnpFull | 64           | 0,1  | 0       | 0011                                  | 00,11 | 0            | 0          |
| WriteNoSnpFull | 64           | 0,1  | 0       | 0011                                  | 10    | 0            | 0,1        |
| WriteNoSnpFull | 64           | 0,1  | 0       | 0000 </br> 0001 </br> 0001 </br> 1101 | 00    | 0            | 0          |
| WriteNoSnpFull | 64           | 0,1  | 0       | 0000 </br> 0001 </br> 0001 </br> 1101 | 10    | 0            | 0,1        |
| WriteNoSnpPtl  | <=64         | 0,1  | 0       | 0010                                  | 11    | 0            | 0          |
| WriteNoSnpPtl  |              |      |         | 0011                                  | 00,11 | 0            | 0          |
| WriteNoSnpPtl  |              |      |         | 0011                                  | 10    | 0            | 0,1        |
| WriteNoSnpPtl  |              |      |         | 0000 </br> 0001 </br> 0101 </br> 1101 | 00    | 0            | 0          |
| WriteNoSnpPtl  |              |      |         | 0000 </br> 0001 </br> 0101 </br> 1101 | 10    | 0            | 0,1        |

Continued on next page