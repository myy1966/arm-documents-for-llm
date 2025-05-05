## B9.2 Sub-packet level

There are two types of error reporting at the sub-packet level:

- B9.2.1 Poison
- B9.2.2 Data Check

### B9.2.1 Poison

The Poison bit is used to indicate that a set of data bytes have previously been corrupted. Passing the Poison bit alongside the data in the DAT packet permits any future user of the data to be notified that the data is corrupt.

When Poison is supported:

- The DAT packet includes one Poison bit per 64 bits of data.
- Data marked as poisoned:

    - Must not be utilized by any Requester.
    - Is permitted, but not required, to be stored in caches and memory if marked as poisoned.

- The Poison value, once set, must be propagated along with the data.
- When a Poison error is detected, it is permitted, but not required, to over poison the data.
- Poison on MTE tags is not supported.

Poison must be accurate if there are any valid bytes in the 64-bit chunk. This is the Poison granularity. When all 8 bytes in the 64-bit chunk are invalid, the Poison bit can take any value.

A Data\_Poison property is used to indicate if a component supports Poison.

> **_NOTE:_** Although Poison on tags is not supported, implementations could choose to do one of the following:
>
> - Poison associated with the data results in the tag being poisoned. Depending on the granularity of the poison associated with the tag, the same techniques that could be used to clear poison associated with data may not clear the poison on the tags.
> - Poison associated with the data does not result in the tag being poisoned. This means that a corrupted tag could subsequently be used in an MTE Match operation, which could incorrectly fail. The rate at which this occurs should be significantly lower than the rate at which data corruption occurs.
> - A mixture of approaches can be used, depending on the caching or storage structures that are used.
>
> Other implementations are possible.

### B9.2.2 Data Check

The DataCheck field is used to detect Data Errors in the DAT packet.

When Data Check is supported:

- The DAT packet carries 8 DataCheck bits per 64 bits of data.
- The Data Check bit is a parity bit that generates Odd Byte parity.