## B1.6 Component naming

The components in the CHI protocol are classified by node type:

**RN**

Request Node. Generates protocol transactions, including reads and writes, to the interconnect. A Request Node is further categorized as:

**RN-F**

Fully Coherent Request Node:

- Includes a hardware-coherent cache.
- Permitted to generate all transactions defined by the protocol.
- Supports all Snoop transactions.

**RN-D**

IO Coherent Request Node with DVM support:

- Does not include a hardware-coherent cache.
- Receives DVM transactions.
- Generates a subset of transactions defined by the protocol.

**RN-I**

IO Coherent Request Node:

- Does not include a hardware-coherent cache.
- Does not receive DVM transactions.
- Generates a subset of transactions defined by the protocol.
- Does not require snoop functionality.

**HN**

Home Node. Node located within the interconnect that receives protocol transactions from Request Nodes. A Home Node is further categorized as:

- **HN-F** Fully Coherent Home Node:

    - Expected to receive all request types, except DVMOp.
    - Includes a Point of Coherence (PoC) that manages coherency by snooping the required RN-Fs, consolidating the Snoop responses for a transaction, and sending a single response to the requesting Request Node.
    - Expected to be the Point of Serialization (PoS) that manages order between memory requests.
    - Could include a directory or snoop filter to reduce redundant snoops.

        > **_NOTE:_** IMPLEMENTATION SPECIFIC, can include an integrated interconnect cache.

- **HN-I** Non-coherent Home Node:

    - Processes a limited subset of request types defined by the protocol.
    - Does not include a PoC and is not capable of processing a Snoopable request. On receipt of a Snoopable request, HN-I must respond with a protocol compliant message.
    - Expected to be the PoS that manages order between IO requests targeting the IO subsystem.

**MN** Miscellaneous Node.

Receives a DVM transaction from a Request Node, completes the required action, and returns a response.
