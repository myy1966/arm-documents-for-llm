- ᵃ Not applicable, SnpAttr bit is used as a Domain Identifier in DVM transactions, see B8.4.1 DVM domain.
- ᵇ Not applicable, can take any value.

The SnpAttr field value in a CMO, in an Atomic, and in ReadNoSnp and ReadNoSnpSep from Home to Subordinate, must be set to 0, irrespective of the field value in the Request from the original Requester to Home. In Write and Combined Write transactions from Home to Subordinate, the bit position for the SnpAttr field is used for the DoDWT field. See B2.3.9.2 Home to Subordinate Write transactions and B2.3.9.4 Home to Subordinate Combined Write and CMO transactions.

> **_NOTE:_** For transactions that can take more than one value of SnpAttr, the value is typically determined from page table attributes.

### B2.7.7 Mismatched Memory attributes

Two different accesses are permitted to occur to the same location using mismatched MemAttr or SnpAttr values. The mismatched MemAttr or SnpAttr values can be expected or unexpected. It is required that the system does not deadlock in either instance and the transaction always makes forward progress.

To assist with the expected mismatched memory attributes, an interconnect:

- Must ensure a Clean line, either UC or SC, in a fully coherent cache is:

    - Not made visible to a Requester using a transaction with SnpAttr = 0 to access that location, if that location has been updated by another transaction with SnpAttr = 0 after the cache line was allocated into the fully coherent cache.
    - Not written to main memory.
    - Not used to overwrite a Dirty copy in a downstream cache.

- Is permitted, but not required, to make a Dirty copy of a cache line that was written by a Requester using a transaction with SnpAttr = 0 visible to a fully coherent Requester. Visibility of the Dirty line must not be removed from the Requester using a transaction with SnpAttr = 0 to access that location.
- Is permitted, but not required, to make a Dirty line, either UD or SD, in a fully coherent cache visible to another Requester using a transaction with SnpAttr = 0 to access that location. Once a Dirty line in a fully coherent cache is made visible to a Requester using a transaction with SnpAttr = 0 request to access that location, the cache line must not be removed from the visibility of that Requester.

> **_NOTE:_** There are multiple implementation options that could be used to ensure that this removal of visibility does not take place. These include, but are not limited to:
>
> - Writing back the dirty copy of the line to main memory.
> - Keeping a copy of the line in the system cache, to be > observed by requests that have SnpAttr = 0.
> - Snooping fully coherent caches to complete requests that have SnpAttr = 0.