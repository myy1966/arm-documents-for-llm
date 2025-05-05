Table B13.17 Continued from previous page

| Size[2:0] | Bytes    |
|-----------|----------|
| 0b100     | 16       |
| 0b101     | 32       |
| 0b110     | 64       |
| 0b111     | Reserved |

### B13.10.24 Memory Attribute, MemAttr

This field is associated with the transaction.

Table B13.18 shows the MemAttr value encodings.

## Table B13.18: MemAttr value encodings

| MemAttr[3:0] | Description                                                                                                                        | 0                                                 | 1                                            |
|--------------|------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------|----------------------------------------------|
| [3]          | Allocate hint bit. Indicates whether or not the cache receiving the transaction is recommended to allocate the transaction         | Recommended that the cache line is not allocated  | Recommended that the cache line is allocated |
| [2]          | Cacheable bit. Indicates a Cacheable transaction for which the cache, when present, must be looked up in servicing the transaction | Non-cacheable. Looking up a cache is not required | Cacheable. Looking up a cache is required    |
| [1]          | Device bit. Indicates if the memory type associated with the transaction is Device or Normal                                       | Normal memory type                                | Device memory type                           |
| [0]          | Early Write Acknowledge (EWA) bit. Specifies the EWA status for the transaction                                                    | EWA not permitted                                 | EWA permitted                                |

See B2.7.3 Memory Attributes.

### B13.10.25 Snoop Attribute, SnpAttr

This field specifies the snoop attribute associated with the transaction.

Table B13.19 shows the SnpAttr value encodings.

Table B13.19: SnpAttr value encodings

| SnpAttr | Description                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------|
| 0       | Non-snoopable </br> An HN-F receiving this request is not expected, but is permitted, to snoop any RN-F nodes. |

Continued on next page