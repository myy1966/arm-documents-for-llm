- B13.10.51 Data payload, Data
- B13.10.52 Critical Chunk Identifier, CCID
- B13.10.53 Data Identifier, DataID
- B13.10.54 Byte Enable, BE
- B13.10.55 Data check, DataCheck
- B13.10.56 Poison
- B13.10.57 Data source, DataSource
- B13.10.58 System Level Caches Replacement Hint, SLCRepHint
- B13.10.59 Reserved for Customer Use, RSVDC

### B13.10.1 Quality of Service, QoS

This field is used to assign a Quality of Service (QoS) value to a transaction. Ascending values of QoS indicate higher priority levels. See B11.1 Quality of Service (QoS) mechanism.

### B13.10.2 Target Identifier, TgtID

This field is the node ID of the component to which the message is targeted. This is used by the interconnect to determine the port to which the message is sent. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.

### B13.10.3 Source Identifier, SrcID

This field is the node ID of the component from which the message is sent. This is used by the interconnect to determine the port from which the message is sent. See B2.4.1 Target Identifier, TgtID, and Source Identifier, SrcID.

### B13.10.4 Home Node Identifier, HomeNID

This field is associated with the original request. The Requester uses the value in this field to determine the TgtID of the CompAck to be sent in response to CompData. See B2.4.11 Home Node Identifier, HomeNID.

Applicable in CompData and DataSepResp.

Inapplicable and must be 0 in all other Data messages.

### B13.10.5 Return Node Identifier, ReturnNID

This field identifies the node to which the Subordinate sends a CompData, DataSepResp, or a Persist response. This field also indicates the node to which the Subordinate sends DBIDResp when DoDWT = 1. The value can be either the node ID of Home or the Requester that originated the transaction. See B2.4.10 Return Node Identifier, ReturnNID.

Applicable from Home to Subordinate in ReadNoSnp, ReadNoSnpSep, CleanSharedPersistSep, WriteNoSnp, WriteNoSnpDef, Combined Write, and Atomic requests.

Inapplicable and must be 0 for all other requests. For Stash requests, the same bits in the packet are used for StashNID.

### B13.10.6 Forward Node Identifier, FwdNID

This field identifies the Requester to which the CompData response can be forwarded. The value must be the NodeID of the Requester that initiated the transaction. See B2.4.12 Forward Node Identifier, FwdNID.