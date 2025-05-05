originally accessed that location.

Table B16.16 shows the Nonshareable\_Cache\_Maint property options.

Table B16.16: Nonshareable\_Cache\_Maint property options

| Nonshareable\_Cache\_Maint value | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| True                             | An RN-F must update all accesses to locations that are marked in the page tables as Non-shareable Cacheable to be Shareable Cacheable. For more information, see B2.7.7 Mismatched memory attributes. </br> An HN-I receiving a request with both SnpAttr and Cacheable asserted must respond with NDERR when completing the transaction, except for when the transaction is a ReadOnce*, WriteUnique, WriteUniqueZero, or an Atomic. </br> An HN-I responding with NDERR upon receiving a ReadOnce*, WriteUnique, WriteUniqueZero, or an Atomic request with both SnpAttr and Cacheable asserted is IMPLEMENTATION DEFINED. </br> When RME_Support property is True, Nonshareable_Cache_Maint property must be True. </br> A system fully supports the cache maintenance of Non-snoopable Cacheable memory when all RN-Fs and the interconnect define the Nonshareable_Cache_Maint property as True. |
| False or Not specified           | There are no additional requirements on an RN-F. </br> An HN-I responding with NDERR upon receiving a request with both SnpAttr and Cacheable asserted is IMPLEMENTATION DEFINED.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

The Nonshareable\_Cache\_Maint property is inapplicable for RN-Is.

### B16.1.18 PBHA\_Support

A PBHA\_Support property determines whether an interface supports PBHA functionality.

Table B16.17 shows the PBHA\_Support property options.

Table B16.17: PBHA\_Support property options

| PBHA\_Support value | Description                                                                                     |
|---------------------|-------------------------------------------------------------------------------------------------|
| True                | PBHA feature is supported. </br> The 4-bit PBHA field is present on REQ, DAT, and SNP channels. |

Continued on next page