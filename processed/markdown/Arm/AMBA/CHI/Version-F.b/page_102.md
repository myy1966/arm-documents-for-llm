- When DoDWT = 0, the ReturnNID can take any value, and the value is not used in any responses.
- When DoDWT = 1, the ReturnNID value is expected to be the original Requester Node ID but is permitted to be the Home Node ID. Used as the TgtID in the DBIDResp response.

In WriteNoSnp with TagOp Match:

- Irrespective of the value of DoDWT, the ReturnNID value is expected to be the original Requester Node ID but is permitted to be the Home Node ID.
- When DoDWT = 0, the ReturnNID value is used as the TgtID in the TagMatch response only.
- When DoDWT = 1, the ReturnNID value is used as the TgtID in the DBIDResp and TagMatch responses.

In WriteNoSnpDef:

- When DoDWT = 0, ReturnNID can take any value, and the value is not used in any response.
- When DoDWT = 1, the ReturnNID value is expected to be the original Requester Node ID but is permitted to be the Home Node ID. Used as the TgtID in the DBIDResp response.

In Non-PCMO Combined Write:

- When DoDWT = 0, ReturnNID can take any value, and the value is not used in any responses.
- When DoDWT = 1, the ReturnNID value is expected to be the original Requester Node ID but is permitted to be the Home Node ID. Used as the TgtID in the DBIDResp response.

In WriteNoSnpFullClnShPer and WriteNoSnpPtlClnShPer:

- Irrespective of the value of DoDWT, the ReturnNID value is expected to be the original Requester Node ID but is permitted to be the Home Node ID.
- When DoDWT = 0, the ReturnNID value is used as the TgtID in the Persist response only.
- When DoDWT = 1, the ReturnNID value is used as the TgtID in the DBIDResp and Persist responses.

### B2.4.11 Home Node Identifier, HomeNID

CompData includes the HomeNID field that is used by the Requester to identify the target of CompAck that the Requester could need to send in response to CompData. HomeNID is applicable in CompData and DataSepResp and is inapplicable and must be set to 0 for all other Data messages.

> **_NOTE:_** There is no functional requirement for the HomeNID and DBID fields in the DataSepResp response because the values that are provided in the RespSepData response are identical and can always be used. However, it is required that these values are included to help with debugging and protocol checking.

### B2.4.12 Forward Node Identifier, FwdNID

A Snoop request from Home to RN-F includes a FwdNID that is used to determine the TgtID for the Data response from the Snoopee. Its value must be the node ID of the original Requester.

The FwdNID field is only applicable in:

- SnpSharedFwd
- SnpCleanFwd
- SnpOnceFwd
- SnpNotSharedDirtyFwd
- SnpUniqueFwd