Table B13.21 Continued from previous page

| LikelyShared | Description                                 |
|--------------|---------------------------------------------|
| 1            | Likely to be shared by another Request Node |

### B13.10.28 Ordering requirements, Order

This field specifies the ordering requirements for a transaction. See B2.6 Ordering for more information on the ordering requirements.

Table B2.9 shows the Order field value encodings.

Table B13.22: Order value encodings

| Order[1:0] | Description          | Permitted between              |
|------------|----------------------|--------------------------------|
| 0b00       | No ordering required | All                            |
| 0b01       | Request accepted     | HN-F to SN-F, and HN-I to SN-I |
| 0b01       | Reserved             | RN to HN                       |
| 0b10       | Request Order/OWO    | RN to HN ᵃ                     |
| 0b10       | Request Order        | HN-I to SN-I                   |
| 0b10       | Reserved             | HN-F to SN-F                   |
| 0b11       | Endpoint Order       | RN to HN, and HN-I to SN-I     |
| 0b11       | Reserved             | HN-F to SN-F                   |

- ᵃ Request Order when ExpCompAck = 0. OWO when ExpCompAck = 1.

### B13.10.29 Exclusive, Excl

This field indicates that the corresponding transaction is an Exclusive-type transaction. The Exclusive bit must only be used with the following transactions:

- ReadNotSharedDirty
- ReadShared
- ReadClean
- ReadPreferUnique
- CleanUnique
- MakeReadUnique
- ReadNoSnp
- WriteNoSnp

Table B13.23 shows the Excl value encodings.