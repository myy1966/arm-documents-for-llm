## B11.5 Page-based Hardware Attributes

Page-based Hardware Attributes (PBHA) is an optional, IMPLEMENTATION DEFINED feature. Support for PBHA on an interface is defined by the PBHA\_Support property. See B16.1.18 PBHA\_Support. PBHA allows software to set up to 4 bits in translation tables, which is then propagated through the memory system with transactions. See B13.10.31 Page-based Hardware Attribute, PBHA.

PBHA values are obtained from page tables during address translations. It is expected, but not required, that all translations to a given PA provide the same PBHA value.

### B11.5.1 PBHA field applicability

On the REQ channel, PBHA is applicable in all requests, except for DVMOp and PCrdReturn where it is inapplicable and must be 0.

On the DAT channel, PBHA is only applicable in SnpRespData, SnpRespDataPtl, and SnpRespDataFwded. The PBHA field is inapplicable and must be set to 0 in all other DAT messages.

On the SNP channel, PBHA is only applicable in Stash snoops. The PBHA field is inapplicable and must be set to 0 in all Non-stash snoops.

### B11.5.2 Interconnect use of PBHA

If the interconnect forwards a request onto the Subordinate, it is expected to forward the PBHA value along with the request.

If the interconnect caches a line, it is expected to cache the PBHA value along with the line. If the line is evicted, it is expected that the PBHA value is forwarded onto the Subordinate.

### B11.5.3 Stash transaction rules

When Home receives a Stash request and generates a Stash snoop to a Requester, it is expected, but not required, that the PBHA value from the request is sent along with the snoop.

The Requester of a DataPull request obtains the address of the request from the received snoop, rather than through an address translation process. Therefore, the Requester is expected, but not required, to obtain the PBHA value from the stash snoop.

### B11.5.4 PBHA value consistency

PBHA values can be added to a request during address translation and propagated through a system if PBHA is supported by downstream components. The PBHA value corresponding to a particular address flowing through the system can be precise or imprecise.

To make a PBHA value precise, the PBHA values used in the request and corresponding responses must be the same as the PBHA values obtained from the address translation. Other considerations include:

- The precise PBHA value is available to the request if caches store PBHA values along with the data when the line is written back to memory. Memory accesses that are the result of cache evictions, dedicated Cache Maintenance Operations, or snoop filter back invalidations must use the PBHA that the entry was cached with, not the PBHA value in any associated request.

    - A CMO that operates on a cache line is also expected to operate on any PBHA value stored along with the line.