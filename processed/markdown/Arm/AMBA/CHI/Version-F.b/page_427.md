    - When responding to a request, the Completer must send the response on the same interface as the one used by the request.
    - A snoop must be sent to the same interface that was used for the transaction that caused the allocation of a cache line.
    - A transaction from one interface must make forward progress without requiring forward progress of a transaction on a duplicate interface.

- All channels must be replicated even when only a subset of the channels needs increased bandwidth.

#### B13.7.1.1 Address striping

An optional optimization is permitted where a Request Node can specify the address striping that is used to select between multiple interfaces. This can be specified for any number of interfaces.

A Request Node is permitted to use address striping to guide its requests to the appropriate interface without declaring the striping algorithm being used.

A Home Node typically can filter snoops based on a snoop filter. If the snoop filter is precise, the node ID of the Requester that cached the cache line is tracked and a snoop is sent for a subsequent request to the same cache line on a single interface. A snoop filter that does not track precisely, or is sized to the number of components in the system instead of the number of Request Node interfaces, is not able to isolate the single interface needed to send the snoop on, unless the snoop filter knows and uses the same address striping algorithm as the Requester.

When a Request Node does not declare its striping algorithm, the snoop filters either need to be larger or the Home must send redundant snoops. It is recommended that a Request Node that uses address striping advertises the striping algorithm in order to be used by the Home Node.

The address striping used by a Request Node can be specified by a hash function.

#### B13.7.1.2 Hash function example

This section describes a suggested hash function to be used to distribute requests across multiple REQ interfaces. The same hash function can be used to distribute snoops across multiple available SNP interfaces. The steps in generating the interface number are:

1. The cache line aligned input address is first filtered through a predefined Hash Mask. The most significant address bits that are not used must be set to all 0 before filtering the address. In this example, the result of the filtering is Mask\_Result.
2. The individual bits of Mask\_Result are XORed to obtain the target interface.

Where the number of interfaces is a power-of-two:

- For 2 interfaces:

Interfaces[0] = Mask\_Result[n-1] ˆ Mask\_Result[n-2] ... Mask\_Result[7] ˆ Mask\_Result[6]

- For 4 interfaces:

Interfaces[1:0] = Mask\_Result[n-1:n-2] ˆ Mask\_Result[n-3:n-4] ... Mask\_Result[9:8] ˆ Mask\_Result[7:6]

- For 8 interfaces:

Interfaces[2:0] = Mask\_Result[n-1:n-3] ˆ Mask\_Result[n-4:n-6] ... Mask\_Result[11:9] ˆ Mask\_Result[8:6]

This example does not cover the situation where the number of interfaces is not a power-of-two.