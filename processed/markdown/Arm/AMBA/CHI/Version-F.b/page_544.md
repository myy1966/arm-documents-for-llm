Page Based Hardware Attributes (PBHA) is an optional, IMPLEMENTATION DEFINED feature. It allows software to set up to two bits in the translation tables, which are then propagated though the memory system with transactions, and can be used in the system to control system components. The meaning of the bits is specific to the system design.

**Peer node**

A protocol node of the same type with reference to itself. For example, the peer node for a Request Node is another Request Node.

**Peer to Peer**

Communication between the same type of nodes. For example, one Request Node to another Request Node.

See also Downstream, Upstream.

**Peripheral Subordinate component**

A Peripheral Subordinate component is also described as a Peripheral Subordinate. It is recommended that a Peripheral Subordinate has an IMPLEMENTATION DEFINED method of access that is typically described in the data sheet for the component. Any access that is not defined as permitted might cause the Peripheral Subordinate to fail, but must complete in a protocol-correct manner to prevent system deadlock. The protocol does not require continued correct operation of the peripheral.

See also Memory Subordinate component, Subordinate component.

**Permission to store**

A component has permission to store if it can perform a store to the associated cache line without informing any other caching Manager or the interconnect.

**Phit**

See Phit.

**PoC**

See PoC.

**PoP**

See PoP.

**PoPA**

See PoPA.

**PoS**

See PoS.

**Prefetching**

Prefetching refers to speculatively fetching instructions or data from the memory system. In particular, instruction prefetching is the process of fetching instructions from memory before the instructions that precede them, in simple sequential execution of the program, have finished executing. Prefetching an instruction does not mean that the instruction has to be executed.

In this specification, references to instruction or data fetching apply also to prefetching, unless the context explicitly indicates otherwise.

**Protocol credit**

See Protocol credit.

**Realm Management Extensions (RME)**