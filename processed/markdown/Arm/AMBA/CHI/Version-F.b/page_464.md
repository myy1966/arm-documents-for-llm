Table B13.38: CCID value encodings

| CCID[1:0] | Critical data chunk |
|-----------|---------------------|
| 0b00      | Data[127:0]         |
| 0b01      | Data [255:128]      |
| 0b10      | Data [383:256]      |
| 0b11      | Data [511:384]      |

### B13.10.53 Data Identifier, DataID

This field indicates the relative position of the data chunk within the 512-bit cache line that is being transferred. See B2.8.4 Data packetization.

Table B13.39 shows the DataID value encodings.

Table B13.39: DataID value encodings

| DataID | Data width </br> 128-bit | Data width </br> 256-bit | Data width </br> 512-bit |
|--------|--------------------------|--------------------------|--------------------------|
| 0b01   | Data [255:128]           | Reserved                 | Reserved                 |
| 0b10   | Data [383:256]           | Data[511:256]            | Reserved                 |
| 0b11   | Data [511:384]           | Reserved                 | Reserved                 |

### B13.10.54 Byte Enable, BE

This field indicates if the byte of data corresponding to this BE bit is valid. The BE field is defined for write data, DVMpayload, and Snoop response data transfers. For Read response data transfers, this field is inapplicable and can take any value. The BE field consists of a bit for each data byte in the DAT flit. See B2.8.3 Byte Enables.

Table B13.40 shows the BE value encodings.

Table B13.40: BE value encodings

| BE | Byte enable                             |
|----|-----------------------------------------|
| 0  | Corresponding byte of data is not valid |
| 1  | Corresponding byte of data is valid     |

### B13.10.55 Data check, DataCheck

This field is used to supply the DataCheck bit for the corresponding byte of Data. See B9.2.2 Data Check.