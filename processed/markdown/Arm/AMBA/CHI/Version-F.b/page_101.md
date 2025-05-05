See Chapter B6 Exclusive accesses for further details.

For other transactions, the LPID value is permitted, but not required, to indicate the original LP that caused a transaction to be issued.

In requests, when applicable, the same bits in the packet are used for TagGroupID, PGroupID, and StashGroupID.

### B2.4.8 Stash Logical Processor Identifier, StashLPID

The StashLPID field can be used to specify a particular LP within the Request Node specified by StashNID, when the corresponding StashLPIDValid bit is asserted. See B13.10.11 Stash Logical Processor Identifier, StashLPID.

See B7.5.1 Supporting REQ packet fields for the permitted combinations of StashLPIDValid and StashNIDValid.

### B2.4.9 Stash Node Identifier, StashNID

The StashNID field provides the Request Node that is the target of the Stash transaction when the corresponding StashNIDValid bit is asserted. See B13.10.9 Stash Node Identifier, StashNID.

### B2.4.10 Return Node Identifier, ReturnNID

A transaction request from Home to Subordinate includes a ReturnNID that is used to determine the TgtID for the following responses from the Subordinate Node:

- Data response
- DBIDResp response
- Persist response
- TagMatch response

Its value must be either the node ID of Home or the node ID of the original Requester.

ReturnNID is only applicable in a ReadNoSnp, ReadNoSnpSep, CleanSharedPersistSep, WriteNoSnp, Combined Write, and Atomic requests from Home to Subordinate. The field is inapplicable and must be set to 0 in all other requests from Home to Subordinate.

ReturnNID is inapplicable and must be set to 0 in all requests from Requester to Home and Requester to Subordinate.

The following are the expected and permitted values for the ReturnNID in requests from the Home Node to the Subordinate Node.

In ReadNoSnp, ReadNoSnpSep, and CleanSharedPersistSep:

- Expected value is the original Requester Node ID but is permitted to be the Home Node ID.
- Used as the TgtID in CompData, DataSepResp and Persist responses.

In Atomic with TagOp Invalid:

- For AtomicStore, ReturnNID can take any value and the value is not used in any responses.
- For Non-store Atomics, the ReturnNID must be the Home Node ID. The value is used as the TgtID in CompData.

In Atomic with TagOp Match:

- ReturnNID must be the Home Node ID.
- The value is used as the TgtID in CompData and TagMatch responses.

In WriteNoSnp with TagOp not Match: