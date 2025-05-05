Table B2.18 shows the permitted data sizes, and the relationship between inbound and outbound valid data size for each Atomic transaction type. The size of the data value returned in response to an AtomicCompare transaction is half the number of bytes specified in the Size field in the associated Request packet.

Table B2.18: Atomic transaction outbound and inbound data sizes

| Atomic transaction   | Outbound (bytes)   | Inbound               |
|----------------------|--------------------|-----------------------|
| AtomicStore          | 1, 2, 4, or 8      | -                     |
| AtomicLoad           | 1, 2, 4, or 8      | Same as outbound      |
| AtomicSwap           | 1, 2, 4, or 8      | Same as outbound      |
| AtomicCompare        | 2, 4, 8, 16, or 32 | Half size of outbound |

#### B2.8.5.2 Address and Data alignment

In the AtomicStore, AtomicLoad, and AtomicSwap transactions:

- The byte address is aligned to the outbound data size.
- The position of data bytes in the NonCopyBackWriteData or any CompData packet matches the endianness of the operation, as specified in the Endian field of the request.
- The big-endian data is byte invariant.

The write data associated with an AtomicCompare transaction is provided in the same way as a transaction that is aligned to the outbound data size.

In the AtomicCompare transaction:

- The byte address must be aligned in the Data packet to the inbound data size, which is equivalent to half the outbound data size.

The two data values in an AtomicCompare transaction are placed in the data field in the following manner:

- The Compare and Swap data values are concatenated and the resulting data payload is aligned in the Data packet to the outbound data size.
- The Compare data is always at the addressed byte location.
- The Swap data is always in the remaining half of the valid data.

For any given Compare data address, the Swap data address can be determined by inverting bit[n] in the Compare data address where:

n = log2 (Compare data size in bytes)

##### B2.8.5.2.1 Alignment example

Figure B2.36 shows the examples of data placement with different addresses and different Data sizes.