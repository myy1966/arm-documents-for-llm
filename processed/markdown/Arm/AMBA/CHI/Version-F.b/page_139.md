## B2.7 Address, Control, and Data

A transaction includes attributes defining the manner in which the transaction is handled by the interconnect. These include the address, memory attributes, snoop attributes, and data formatting. Each attribute is defined in this section.

In this section, unless explicitly stated otherwise, a reference to a Write transaction includes both the individual Write transaction and the corresponding Combined Write transaction.

### B2.7.1 Address

The CHI protocol supports:

- Physical Address (PA) of 44 bits to 52 bits, in 1 bit increments.
- Virtual Address (VA) of 49 bits to 53 bits.

The REQ and SNP packet Addr fields are specified as follows:

- REQ channel: Address[(MPA-1):0]
- SNP channel: Address[(MPA-1):3]

MPA is the Maximum PA supported.

Table B2.10 shows the relationship between the physical address field width and the supported virtual address.

Table B2.10: Addr field width and supported Physical Address and Virtual Address size

|                             | Maximum supported (bits)   | Maximum supported (bits)   |
|-----------------------------|----------------------------|----------------------------|
| REQ Addr field width (bits) | Physical Address           | Virtual Address            |
| 44                          | 44                         | 49                         |
| 45                          | 45                         | 51                         |
| 46 to 52                    | 46 to 52                   | 53                         |

See B8.3 DVMOp field value restrictions for DVM payload mapping in the REQ and SNP fields with different Addr field widths.

The Req\_Addr\_Width parameter is used to specify the maximum PA in bits that is supported by a component. Valid values for this parameter are 44 to 52, when not specified, the parameter takes the default value of 44.

### B2.7.2 Physical Address Space, PAS

The PAS of an access is determined using a combination of the NSE and NS fields. Table B2.11 shows the encoding for the PAS.

Table B2.11: Physical Address Space encodings

|   [NSE, NS] | Description   |
|-------------|---------------|
|          00 | Secure        |
|          01 | Non-secure    |

Continued on next page