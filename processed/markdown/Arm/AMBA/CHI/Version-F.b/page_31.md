**PoDP**

Point of Deep Persistence (PoDP) is a point in the memory system where the data is preserved even when the power and the back up battery fail simultaneously.

**PoPA**

Point of Physical Aliasing (PoPA) is a point where updates to a location in one Physical Address Space (PAS) are visible to all other Physical Address Spaces.

**Downstream cache**

A downstream cache is defined from the perspective of a Request Node. A downstream cache for a Request is a cache that the Request accesses using CHI request transactions. A Request Node can send a request with data to allocate data into a downstream cache.

**Requester**

A component that starts a transaction by issuing a request message. The term Requester can be used for a component that independently initiates transactions. The term Requester can also be used for an interconnect component that issues a downstream Request message independently or as a side-effect of other transactions that are occurring in the system.

**Completer**

Any component that responds to a received transaction from another component. A Completer can either be an interconnect component, such as a Home Node or a Miscellaneous Node, or a component, such as a Subordinate, that is outside of the interconnect.

**Subordinate**

An agent that receives transactions and completes them appropriately. Typically, a Subordinate is the most downstream agent in a system. A Subordinate can also be referred to as a Completer or Endpoint.

**Endpoint**

Another name for a Subordinate component. An Endpoint is the final destination for a transaction.

**Protocol Credit**

A credit, or guarantee, from a Completer that it will accept a transaction.

**Link layer Credit**

A credit, or guarantee, that a flit will be accepted on the other side of the link. An L-Credit is a credit for a single hop at the Link layer.

**ICN**

Interconnect (ICN) is the CHI transport mechanism that is used for communication between protocol nodes. An interconnect can include an IMPLEMENTATION DEFINED fabric of switches connected in a ring, mesh, crossbar, or another topology. The interconnect can also include protocol nodes, such as Home Node and Miscellaneous Node.

**IPA**

Intermediate Physical Address (IPA). In two-stage address translation:

- Stage 1 provides an Intermediate Physical Address (IPA).
- Stage 2 provides the Physical Address (PA).

**RN**

Request Node (RN) generates protocol transactions, including reads and writes, to the interconnect.

**HN**