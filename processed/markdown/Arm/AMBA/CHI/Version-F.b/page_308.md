> From initial system reset, the first LP to perform an Exclusive Store transaction can be successful, but it is not required. At that point, all other LPs must subsequently register the start of their exclusive sequence for their Exclusive Store transaction to be successful.
>
> When an Exclusive Store transaction from one LP passes and the registered attempts of all other LPs is reset, the other LPs can only register a new exclusive sequence after the CompAck response is observed for the Exclusive Store transaction that passed.

> **_NOTE:_** An LP and PoC monitor pair are required to support an Exclusive access to a Snoopable memory location.

### B6.2.2 Additional address comparison

The PoC monitor can be enhanced to include some address comparison. A full address comparison is not required and it is permitted to only record a subset of address bits. This approach reduces the chances of an Exclusive Store transaction failing because of an Exclusive Store transaction from another LP to a different address location. The number of bits of address comparison used is IMPLEMENTATION DEFINED.

Where an additional address comparison monitor is used, the monitored address bits are recorded at the start of an exclusive sequence on either a Load Exclusive or Store Exclusive transaction. The monitor is reset by a successful Exclusive Store transaction from another LP to a matching address.

A monitor that includes an additional address comparison must still include a minimum monitor of a single bit for every Exclusive-capable LP to ensure forward progress.

An Exclusive Store transaction is permitted to progress if one of the following occurs:

- The address monitor has registered an exclusive sequence for a matching address from the same LP and has not been reset by an Exclusive Store transaction from a different LP with a matching address.
- The minimum single-bit monitor has been set by an exclusive sequence from the same LP and it has not been reset by an Exclusive Store transaction from a different LP to any address.

> **_NOTE:_** The term matching address is used to describe where a monitor only records a subset of address bits. The address bits that are recorded are identical, but the address bits that are not recorded can be different.
>
> An implementation does not require an address monitor for each Exclusive-capable LP. Because the address monitor provides a performance enhancement, it is acceptable to have fewer address monitors and for the use of these to be IMPLEMENTATION DEFINED. For example, address monitors can be used on a first-come first-served basis, or by allocation to particular Logical Processors. Alternatively, a more complex algorithm could be implemented.
>
> Additional PoC exclusive monitor functionality can be provided to prevent interference, or denial of service, caused by one agent in the system issuing many Exclusive access transactions. It is recommended that the progress on Exclusive requests from one PAS is independent of progress on Exclusive requests from any other PAS.

### B6.2.3 Alternatives to a PoC monitor

An HN-F is permitted to use the following mechanisms instead of a PoC monitor to determine the results of an Exclusive access:

- A precise Snoop Filter, to track if the Requester at the time of Exclusive Store processing retains a copy of the cache line.