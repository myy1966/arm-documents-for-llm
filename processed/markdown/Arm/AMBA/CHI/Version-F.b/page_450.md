The CHI protocol supports a PA of 44 to 52 bits. The address is carried in Addr field in the REQ and SNP channel.

The width of the field is defined by the Req\_Addr\_Width parameter. The field width is the same value of the parameter in REQ channel, Addr[(43-51):0], and is three less than the parameter value in the SNP channel, Addr[(43-51):3].

The Addr field is utilized in the REQ and SNP channels in the following manner.

- For Read, PrefetchTgt, Dataless, Write, and Atomic transactions, the Addr field includes the address of the memory location being accessed. This starts with Addr[0] mapped to bit 0 of Addr.
- For a snoop request, except SnpDVMOp, the Addr field includes the address of the location being snooped. This starts with Addr[3] mapped to bit 0 of Addr.

    - Addr[(43-51):6] is the cache line address. It is sufficient to uniquely identify the cache line to be accessed by the snoop.
    - Addr[5:4] identifies the critical chunk being accessed by the transaction. See B2.8.6 Critical Chunk Identifier. It is recommended that the snooped cache returns the data in wrap order with the critical chunk returned first.

> **_NOTE:_** Addr[3] in the REQ channel, that is Addr[0] in SNP channel, is supplied but is not used by a snoop request.

- For a DVMOp and SnpDVMOp request, the Addr field is used to carry information related to a DVM operation. See Chapter B8 DVM Operations.
- The Addr value is not used for PCrdReturn transaction and must be set to 0.

### B13.10.21 Non-secure, NS

This field is combined with NSE to establish the PAS of an access. See B2.7.2 Physical Address Space, PAS.

### B13.10.22 Non-secure extension, NSE

This field is combined with NS to establish the PAS of an access. See B2.7.2 Physical Address Space, PAS.

### B13.10.23 Size of transaction data, Size

This field specifies the size of the data associated with the transaction. See B2.8.1 Data size.

Table B13.17 shows the Size field value encodings.

Table B13.17: Size field value encodings

| Size[2:0] | Bytes |
|-----------|-------|
| 0b000     | 1     |
| 0b001     | 2     |
| 0b010     | 4     |
| 0b011     | 8     |

Continued on next page