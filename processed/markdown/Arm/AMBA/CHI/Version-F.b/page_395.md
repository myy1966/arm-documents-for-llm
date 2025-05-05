## B12.2 Message extensions

The following extensions to the CHI message definitions are used to support Memory Tagging:

**Tag**

Provides sets of 4-bit tags, each associated with an aligned 16 bytes of data.

- Applicable on the DAT channel only.
- Size is Data\_Width/32 bits.

See Tag.

**TU**

Tag Update. Indicates which of the Allocation Tags must be updated.

- Applicable on the DAT channel only.
- Size is Data\_Width/128 bits.

See TU.

**TagOp**

Tag Operation. Indicates the operation to be performed on the tags present in the corresponding DAT channel.

- Applicable on the REQ, DAT, and RSP channels.
- Size is 2 bits.
- Table B13.31 shows the value encodings.

Table B12.1: TagOp encodings and Tag operations

| TagOp[1:0] | Tag operation  |
|------------|----------------|
| 0b00       | Invalid        |
| 0b01       | Transfer       |
| 0b10       | Update         |
| 0b11       | Match or Fetch |

See TagOp.

> **_NOTE:_** For clarity, in the following sections TagOp values are italicized to differentiate them from data and cache line values.
