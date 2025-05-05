## B2.8 Data transfer

A data payload is included in Read transactions, Write transactions, Combined Write transactions, Atomic transactions, and Snoop responses with data. This section defines the data alignment rules and the data bytes that are accessed for different combinations of address, transaction size, and memory type.

In this section, unless explicitly stated otherwise, a reference to a Write transaction includes both the individual Write transaction and the corresponding Combined Write transaction.

### B2.8.1 Data size

The Size field in a packet is used, in combination with other fields, to determine the number of bytes transferred.

Table B2.16 shows the Size field value encodings. Snoop transactions do not include a Size field. All snoop data transfers are 64-byte.

Table B2.16: Size field value encodings

| Size[2:0]   | Bytes    |
|-------------|----------|
| 0b000       | 1        |
| 0b001       | 2        |
| 0b010       | 4        |
| 0b011       | 8        |
| 0b100       | 16       |
| 0b101       | 32       |
| 0b110       | 64       |
| 0b111       | Reserved |

### B2.8.2 Bytes access in memory

The MemAttr[1] bit field determines if the memory type is Device or Normal. See B2.7.3 Memory Attributes. The bytes that are accessed are determined by the memory type as follows:

**Normal memory**

Transactions with a Normal memory type access the number of bytes defined by the Size field. Data access is from the Aligned\_Address, that is, the transaction address rounded down to the nearest Size boundary and ends at the byte before the next Size boundary.

This is calculated as:

Start\_Address = Addr field value.

Number\_Bytes = 2^Size field value.

INT(x) = Rounded down integer value of x.

Aligned\_Address = (INT(Start\_Address / Number\_Bytes)) x Number\_Bytes.

The bytes accessed are from (Aligned\_Address) to (Aligned\_Address + Number\_Bytes) - 1.


**Device memory**

Transactions with a Device memory type access the number of bytes from the transaction address up to the byte before the next Size boundary. The bytes accessed are from (Start\_Address) to (Aligned\_Address + Number\_Bytes) - 1.
