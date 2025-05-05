## B3.3 TgtID determination

This section describes how the TgtID is determined for the different message types. It contains the following sections:

- B3.3.1 TgtID determination for Request messages
- B3.3.2 TgtID determination for Response messages
- B3.3.3 TgtID determination for snoop request messages

### B3.3.1 TgtID determination for Request messages

For mapping of TgtID in requests from the Request Node, it is required that the SAM logic is present in the Request Node or in the interconnect. In the case of the interconnect, the TgtID could be remapped in the Request packet provided by the Request Node.

The TgtID of a Request message is determined in the following manner using the SAM logic.

Except for PCrdReturn:

- If the request does not use a pre-allocated credit, the TgtID is determined by:

    - Opcode for DVMOp.
    - Address to node ID mapping for all other requests. PrefetchTgt uses a different Address to node ID mapper than other requests. Two requests from a Request Node to the same Address, where one is a PrefetchTgt, target different nodes. PrefetchTgt always targets a Subordinate Node. All other requests from a Request Node that use an Address to node ID mapper target a Home Node.

- If the request uses pre-allocated credit, the TgtID of the Request must be obtained from either the SrcID of the RetryAck, provided as a response to the original Request message, or the TgtID of the original request.

For PCrdReturn:

- The TgtID provided by the Request Node must match the SrcID included in the prior PCrdGrant which provided the credit being returned.

A Request Node must expect the interconnect to remap the TgtID of a request.

For transactions from a Request Node, except for PrefetchTgt which is targeted to an SN-F, it is expected a Snoopable transaction to be targeted to HN-F and a Non-snoopable transaction to target HN-I or HN-F. It is legal for a Snoopable transaction to be targeted at an HN-I, for example, due to a software programming error. In this case, the HN-I is required to respond to the transaction in a protocol-compliant manner, but coherency is not guaranteed.

A Home Node could also use address map logic to determine the target Subordinate Node ID for each request.

### B3.3.2 TgtID determination for Response messages

Response packets are issued as a result of a received message. The TgtID in Response packets must match either the SrcID, HomeNID, ReturnNID, or FwdNID in the received message that resulted in the response being sent.

Table B3.1 shows the source of the Response packet TgtID for each Response message type and the field in the received message that determines the TgtID.