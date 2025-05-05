Table B2.11 Continued from previous page

|   [NSE, NS] | Description   |
|-------------|---------------|
|          10 | Root          |
|          11 | Realm         |

For Snoopable transactions, the PAS can be considered additional address information that defines four address spaces. Any aliasing between the different Physical Address Spaces must be handled correctly.

> **_NOTE:_** Hardware coherency does not manage coherency between the four address spaces. See B2.6.1 Multi-copy atomicity.

The PAS encoding requirements are:

- Can take any value in any Read, Dataless, Write, and Atomic transactions.
- Can take any value in PrefetchTgt transaction.
- Is not applicable in the DVMOp or PCrdReturn transaction, and must be set to 0.

### B2.7.3 Memory Attributes

The Memory Attributes (MemAttr) consist of Early Write Acknowledgment (EWA), Device, Cacheable, and Allocate.

#### B2.7.3.1 EWA

EWA indicates whether the Write completion response for a transaction:

- Can come from an intermediate point in the interconnect, such as a Home Node.
- Must come from the final endpoint at the target destination.

If EWA is asserted, the Write completion response for the transaction can come from an intermediate point or from the endpoint. A completion that comes from an intermediate point must provide the same guarantees required by a Comp as described in B2.6.2 Completion response and ordering.

If EWA is deasserted, the write completion response for the transaction must come from the endpoint.

> **_NOTE:_** It is permitted, but not required, for an implementation not to use the EWA attribute. In this instance, completion must be given from the endpoint.

The EWA assertion requirements are:

- Can take any value in:

    - A ReadNoSnp and ReadNoSnpSep transaction
    - A WriteNoSnp and WriteNoSnpDef transaction.

> **_NOTE:_** For a WriteNoSnpDef transaction, it is expected that the response comes from the final target endpoint, regardless of EWA value.