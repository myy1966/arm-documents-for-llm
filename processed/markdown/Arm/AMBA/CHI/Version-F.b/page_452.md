Table B13.19 Continued from previous page

| SnpAttr | Description                                                                                                                                                                                                                                                                                                                                                                                                              |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1       | Snoopable </br> An HN-F receiving this request might need to send appropriate snoops to any RN-F nodes that could have the cache line. </br> This could implicate all, certain, or no RN-F nodes, if the HN-F does not have a snoop filter. Snoops are not required as a result of CopyBack transactions. </br> The response given by an HN-I receiving this request is detailed in B16.1.17 Nonshareable\_Cache\_Maint. |

See B2.7.6 Snoop attribute.

### B13.10.26 Do Direct Write Transfer, DoDWT

The characteristics of this field are:

- Only applicable in WriteNoSnpPtl, WriteNoSnpFull, WriteNoSnpDef, and Combined Write requests from Home to Subordinate.
- Inapplicable and must be set to 0 in all other requests.
- The bit shares the same field as SnpAttr.

Table B13.20 shows the DoDWT value encodings.

Table B13.20: DoDWT value encodings

| DoDWT | DBIDResp.TgtID value                      | DBIDResp.TxnID value                    |
|-------|-------------------------------------------|-----------------------------------------|
| 0     | Set to the SrcID value of the request     | Set to TxnID value in the request       |
| 1     | Set to the ReturnNID value in the request | Set to ReturnTxnID value in the request |

See B2.3.2.1 Immediate Write and B2.3.2.4 Combined Immediate Write and CMO.

### B13.10.27 Likely Shared, LikelyShared

This field indicates whether the requested data is likely to be shared with another Request Node. See B2.7.5 Likely Shared.

Table B13.21 shows the LikelyShared field value encodings.

Table B13.21: LikelyShared value encodings

| LikelyShared | Description                                     |
|--------------|-------------------------------------------------|
| 0            | Not likely to be shared by another Request Node |

Continued on next page