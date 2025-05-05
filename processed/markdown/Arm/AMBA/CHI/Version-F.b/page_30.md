## B1.3 Terminology

The following terms have a specific meaning within this specification:

**Transaction**

A transaction carries out a single operation. Typically, a transaction either reads from memory or writes to memory.

**Message**

A message is a protocol layer term that defines the granule-of-exchange between two components. Examples are:

- Request
- Data response
- Snoop request

A single Data response message can be made up of a number of packets.

**Packet**

A packet is the granule-of-transfer over the interconnect between endpoints. A message could be made up of one or more packets. For example, a single Data response message can be made up of 1 to 4 packets. Each packet contains routing information, such as destination ID and source ID, allowing for independent routing over the interconnect.

**Flit**

FLow control unIT (Flit) is the smallest flow control unit. A packet can be made up of one or more flits. All the flits of a given packet follow the same path through the interconnect.

> **_NOTE:_** For CHI, all packets consist of a single flit.

**Phit**

PHysical layer transfer unIT (Phit) is one transfer between two adjacent network devices. A flit can be made up of one or more phits.

> **_NOTE:_** For CHI, all flits consist of a single phit.

**PoS**

Point of Serialization (PoS) is a point within the interconnect where the ordering between requests from different agents is determined.

**PoC**

Point of Coherence (PoC) is a point at which all agents that can access memory are guaranteed to see the same copy of a memory location. In a typical CHI-based system, the PoC is the HN-F in the interconnect.

**PoP**

Point of Persistence (PoP) is a potential point in a memory system at or beyond the Point of Coherency, where a write to memory is maintained when system power is removed, and reliably recovered when power is restored to the affected locations in memory.