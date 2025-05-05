Table B13.23: Excl value encodings

| Excl | Description           |
|------|-----------------------|
| 0    | Normal transaction    |
| 1    | Exclusive transaction |

See B6.3 Exclusive transactions.

### B13.10.30 CopyAtHome, CAH

This field indicates:

- In responses from a Home or a Snoopee: whether the Home has a copy of the cache line that is provided to the Requester.
- In CopyBack requests to Home: the Requester has not modified the line or MTE tags since Home indicated keeping a copy of the line.

The CAH attribute does not affect the normal operation of the Requester regarding Clean or Dirty lines. CAH is only used to influence whether a data transfer is required when executing a CopyBack transaction.

Applicable and can take any value in:

- All CopyBack and Combined CopyBack Write requests, except WriteBackPtl
- CompData and DataSepResp responses to the Requester
- SnpRespData and SnpRespDataFwded

Applicable and must be set to 0 in:

- WriteBackPtl
- SnpRespDataPtl

Inapplicable and must be set to 0 in all other messages.

See B2.3.2.3 CopyBack Write and B2.7.8 CopyAtHome attribute for more information.

### B13.10.31 Page-based Hardware Attribute, PBHA

This field carries 4 bits from the translation tables that can be used for IMPLEMENTATION DEFINED hardware control. See B11.5 Page-based Hardware Attributes.

Support for PBHA on an interface is defined by PBHA\_Support property. See B16.1.18 PBHA\_Support.

When supported, the PBHA field is present on REQ, DAT, and SNP channels:

- On the REQ channel, PBHA is applicable in all requests, except for DVMOp and PCrdReturn where it is inapplicable and must be set to 0.
- On the DAT channel, PBHA is only applicable in SnpRespData, SnpRespDataPtl, and SnpRespDataFwded. The PBHA field is inapplicable and must be set to 0 in all other DAT messages.
- On the SNP channel, PBHA is only applicable in Stash snoops. The PBHA field is inapplicable and must be set to 0 in all Non-stash snoops.

The PBHA field is not present in RSP channel.
