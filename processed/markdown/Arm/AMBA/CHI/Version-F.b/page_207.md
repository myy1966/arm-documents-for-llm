    - The target returns the completion response with data. The data value is the original value at the addressed location.
    - Number of operations supported is 1.

Other common characteristics of Atomic transactions are:

- Data must be included in the completion response to the Requester, except for AtomicStore transaction. For AtomicStore, the completion response does not include the data response.

    - When data is returned, inbound data size must be the same as the outbound data size, except for an AtomicCompare transaction. In AtomicCompare, inbound data size must be half of the outbound data size.
    - The data value in the response data must be the original value at the addressed location.
    - The received data must not be cached at the Requester.

- BE bits must be asserted for all valid data in the outbound data messages. BE bits for inbound data are inapplicable and can take any value.
- The request can result in a cache state change at other Request Nodes in the system. The peer Request Node cache state must be Invalid at the completion of the request.
- Atomic transactions cannot use DMT nor DWT flows.

A Requester that must perform an atomic operation on a cached copy of the line can do the following if the cache line is:

- Unique. The atomic operation can be peformed locally without generating an Atomic transaction.
- Shared but not Dirty. The Requester can either:

    - Generate a ReadUnique, CleanUnique, or MakeReadUnique to gain ownership of the cache line and perform the atomic operation locally.
    - Invalidate the local copy and send the Atomic transaction to the interconnect.

- Shared Dirty. The Requester can either:

    - Generate a ReadUnique, CleanUnique, or MakeReadUnique, gain ownership of the cache line, and perform the operation locally.
    - WriteBack and Invalidate the local copy and subsequently send the Atomic transaction to the interconnect.

- Optionally, in all the above cases, the Requester is permitted, but not required, to send the Atomic transaction with the SnoopMe bit set to direct the interconnect to send a Snoop request to the Requester to invalidate, and if necessary, extract the cached copy. See B13.10.35 SnoopMe.

#### B4.2.5.2 Atomic request attribute values

This section discusses the attribute values for Atomic requests across node interfaces.

Table B4.22 lists the permitted values for attributes for Atomic requests from Request Node to Home Node.