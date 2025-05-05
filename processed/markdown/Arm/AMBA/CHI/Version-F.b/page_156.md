## B2.8.3.3 Snoop transactions

For Snoop responses with data that use the SnpRespData or SnpRespDataFwded opcode, all BE bits must be asserted.

For Snoop responses with data that use the SnpRespDataPtl opcode, any combination of BE bits can be asserted alongside the data transfers. This includes asserting all and asserting none.

### B2.8.4 Data packetization

For each transaction that involves data, the data bytes can be transferred in multiple packets.

The number of packets required is determined by:

- Number of bytes
- Data bus width

The number of bytes transferred in each packet is determined by:

- Data bus width

The CHI protocol supports the following data bus widths:

- 128-bit
- 256-bit
- 512-bit

The Data Identifier (DataID) and Critical Chunk Identifier (CCID) fields are used to identify data packets within a transaction.

A transaction size of up to 16-byte is always contained in a single packet. The DataID can be calculated for each packet based on the data bus width:

- 128-bit: bits [5:4] of the effective memory address of any byte in the packet
- 256-bit: bit [5] of the effective memory address of any byte in the packet, concatenated with 0b0
- 512-bit: always 0b00

For different data bus widths, Table B2.17 shows the relationship between the DataID field and the bytes that are contained within the packet.

Table B2.17: DataID and the bytes within a packet for different data widths

| DataID   | Data Width 128-bit   | 256-bit       | 512-bit     |
|----------|----------------------|---------------|-------------|
| 0b00     | Data[127:0]          | Data[255:0]   | Data[511:0] |
| 0b01     | Data[255:128]        | Reserved      | Reserved    |
| 0b10     | Data[383:256]        | Data[511:256] | Reserved    |
| 0b11     | Data[511:384]        | Reserved      | Reserved    |

Within a data packet, all bytes are located at their natural byte positions. This is true even if fewer data bytes are transferred than the width of the data bus.

The number of data packets used for transactions to Device memory is independent of the address of the transaction. The number of data packets required is determined only by the Size field and the data bus width.