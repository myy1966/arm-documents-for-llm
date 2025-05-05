## B1.1 Architecture overview

The CHI architecture is a scalable, coherent hub interface and on-chip interconnect used by multiple components. The CHI architecture allows for flexible topologies of component connections, driven by performance, power, and area system requirements.

### B1.1.1 Components

The components of CHI-based systems can comprise of:

- Standalone processors
- Processor clusters
- Graphic processors
- Memory controllers
- I/O bridges
- PCIe subsystems
- Interconnects

### B1.1.2 Key features

The key features of the architecture are:

- Scalable architecture, enabling modular designs that scale from small to large systems.
- Independent layered approach, comprising of Protocol, Network, and Link layer, with distinct functionalities.
- Packet-based communication.
- All transactions handled by an interconnect-based Home Node that co-ordinates required snoops, cache, and memory accesses.
- The CHI coherence protocol supports:

    - Coherency granule of 64-byte cache line.
    - Snoop filter and directory-based systems for snoop scaling.
    - Both MESI and MOESI cache models with forwarding of data from any cache state.
    - Additional partial and empty cache line states.

- The CHI transaction set includes:
- Enriched transaction types that permit performance, area, and power efficient system cache implementation.

    - Support for atomic operations and synchronization within the interconnect.
    - Support for the efficient execution of Exclusive accesses.
    - Transactions for the efficient movement and placement of data, to move data in a timely manner closer to the point of anticipated use.
    - Virtual memory management through Distributed Virtual Memory (DVM) operations.

- Request retry to manage protocol resources.
- Support for end-to-end Quality of Service (QoS).
- Support for the Arm Memory Tagging Extension (MTE).
- Support for the Arm Realm Management Extension (RME).