- Configurable data width to meet the requirements of the system.
- ARM TrustZone™ support on a transaction-by-transaction basis.
- Optimized transaction flow for coherent writes with a producer-consumer ordering model.
- Error reporting and propagation across components and interconnect for system reliability and integrity.
- Handling sub cache line Data Errors using Data Poisoning and per byte error indication.
- Power-aware signaling on the component interface:

    - Enabling flit-level clock gating.
    - Component activation and deactivation sequence for clock-gate and power-gate control.
    - Protocol activity indication for power and clock control.

### B1.1.3 Architecture layers

Functionality is grouped into the following layers:

- Protocol
- Network
- Link

Table B1.1 describes the primary function of each layer.

Table B1.1: Layers of the CHI architecture

| Layer    | Communication granularity | Primary function |
|----------|---------------------------|------------------|
| Protocol | Transaction               | The Protocol layer is the topmost layer in the CHI architecture. The function of the Protocol layer is to: - Generate and process requests and responses at the protocol nodes. - Define the permitted cache state transitions at the protocol nodes that include caches. - Define the transaction flows for each request type. - Manage the protocol level flow control. The function of the Network layer is to: - Packetize the protocol message. |
| Network  | Packet                    | - Determine the source and target node IDs required to route the packet over the interconnect to the required destination and add to the packet. |
| Link     | Flit                      | The function of the Link layer is to: - Provide flow control between network devices. - Manage link channels to provide deadlock-free switching across the network. |