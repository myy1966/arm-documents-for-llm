the Realm Management Extension (RME) is an extension to the Armv9 A-profile architecture. RME is one component of the Arm Confidential Computer Architecture (CCA). Together with the other components of the Arm CCA, RME enables support for dynamic, attestable. and trusted execution environments, Realms, to be run on an Arm PE. RME adds two additional Security states, Root and Realm, and two physical address spaces, Root and Realm, and provides hardware-based isolation that allows execution contexts to run in different Security states and share resources in the system.

**Requester**

See Requester.

**Requester component**

A component that initiates transactions.

It is possible that a single component can act as both a Requester component and as a Subordinate component. For example, a Direct Memory Access (DMA) component can be a Manager component when it is initiating transactions to move data, and a Subordinate component when it is being programmed.

See also Component, Interconnect component, Subordinate component.

**RN**

See RN.

**Signed**

A value with Two's complement notation, unless otherwise stated.

**SN**

See SN.

**Snoop filter**

A precise snoop filter that is able to track precisely the cache lines that might be allocated within a Requester.

**Snooped cache**

A hardware-coherent cache that receives Snoop transactions.

**Speculative read**

A transaction that a Manager issues when it might not need the transaction to be performed because it already has a copy of the accessed cache line in its local cache. Typically, a Manager issues a speculative read in parallel with a local cache lookup. This gives lower latency than looking in the local cache first, and then issuing a read transaction only if the required cache line is not found in the local cache.

See also Load.

**Stash**

The action of placing data in a cache closer to the agent that is expected to be the next user of the data.

**Store**

The action of a Requester component changing the value held at a particular address location. For a processor, a store occurs as the result of executing a particular instruction. Whether the store results in the Requester issuing a read or write transaction depends on whether the accessed cache line is held in the local cache, and if it is in the local cache, the state it is in.

**Subordinate**

An agent that agent that receives and responds to requests.

**Subordinate component**