# Chapter B5 Interconnect Protocol Flows

This chapter shows interconnect protocol flows for different transaction types, and interconnect hazard conditions. The protocol flows are illustrated using Time-Space diagrams. It contains the following sections:

- B5.1 Read transaction flows
- B5.2 Dataless transaction flows
- B5.3 Write transaction flows
- B5.4 Atomic transaction flows
- B5.5 Stash transaction flows
- B5.6 Hazard handling examples

See Figure 2 for details of the conventions used to illustrate protocol flow.

In the transaction flow diagrams that follow:

- There are multiple coherent Request Nodes, an HN-F, and an SN-F.
- If the HN-F receives multiple data responses, that is, one response from a snooped RN-F and another from an SN-F, the data being forwarded to the Requester is highlighted in bold.
- There is no interconnect cache at the HN-F. This results in all requests to the HN-F initiating a request to the SN-F.