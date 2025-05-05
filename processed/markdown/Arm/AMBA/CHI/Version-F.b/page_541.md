A set of signals grouped together to communicate a particular set of messages between a Requester and Completer pair. For example, Request channel is used to communicate request messages.

A channel consists of a set of information signals and a separate Valid and Credit signal to provide the channel handshake mechanism.

**Coherency granule**

The minimum size of the block of memory affected by any coherency consideration. For example, an operation to make two copies of an address coherent makes the two copies of a block of memory coherent, where that block of memory is:

- At least the size of the coherency granule
- Aligned to the size of the coherency granule.

See also Cache line.

**Coherent**

Data accesses from a set of observers to a memory location are coherent accesses to that memory location by the members of the set of observers are consistent with there being a single total order of all writes to that memory location by all members of the set of observers.

**Completer**

See Completer.

**Component**

A distinct functional unit that has at least one AMBA interface. Component can be used as a general term for Manager, Subordinate, peripheral, and interconnect components.

See also Interconnect component, Requester component, Memory Subordinate component, Peripheral Subordinate component, Subordinate component.

**Deprecated**

Something that is present in the specification for backwards compatibility. Whenever possible you must avoid using deprecated features. These features might not be present in future versions of the specification.

**Device**

See Peripheral Subordinate component.

**Direct Write Transfer**

Sending Read data directly from a Snoopee or Subordinate to the Requester bypassing the Home Node.

**Downstream**

A transaction operates between a Requester component and one or more Subordinate components, and can pass through one or more intermediate components. At any intermediate component, for a given transaction, downstream means between that component and a destination Subordinate component, and includes the destination Subordinate component.

Downstream and upstream are defined relative to the transaction as a whole, not relative to individual data flows within a transaction.

See also Requester component, Peer to Peer, Subordinate component, Upstream.

**Downstream cache**

See Downstream cache.

**Endpoint**

See Endpoint.
