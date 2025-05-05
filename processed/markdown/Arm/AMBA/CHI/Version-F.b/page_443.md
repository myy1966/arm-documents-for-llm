### B13.10.10 Stash Node Identifier Valid, StashNIDValid

This field indicates if StashNIDValid field has a valid value. See B7.4 Stash target identifiers.

Applicable in Stash requests, inapplicable and must be set to 0 in all other requests.

Table B13.10 shows the StashNIDValid value encodings.

Table B13.10: StashNIDValid value encodings

| StashNIDValid | Description                                               |
|---------------|-----------------------------------------------------------|
| 0             | StashNID field value is inapplicable and must be set to 0 |
| 1             | StashNID field in the Request has a valid Stash target    |

For permitted combinations of StashNIDValid and StashLPIDValid, see Table B7.3.

### B13.10.11 Stash Logical Processor Identifier, StashLPID

This field provides a valid LP target value within the Request Node specified by StashNID. See B7.4 Stash target identifiers.

Applicable in Stash requests and Stash type Snoop requests.

Inapplicable and must be 0 for all other requests. For ReadNoSnp requests, the same bits in the packet are used for ReturnTxnID.

Inapplicable and must be 0 for all other snoop requests. For Forwarding snoops, the same bits in the packet are used for FwdTxnID and for SnpDVMOp snoops the same bits in the packet are used for VMIDExt.

### B13.10.12 Stash Logical Processor Identifier Valid, StashLPIDValid

This field indicates if the StashLPID field has a valid value. See B7.4 Stash target identifiers.

Applicable in Stash requests and Stash snoop requests, inapplicable and must be set to 0 in all other requests.

Table B13.11 shows the StashLPIDValid value encodings.

Table B13.11: StashLPIDValid value encodings

| StashLPIDValid | Description                                                |
|----------------|------------------------------------------------------------|
| 0              | StashLPID field value is inapplicable and must be set to 0 |
| 1              | StashLPID field in the Request has a valid Stash target    |

For permitted combinations of StashLPIDValid and StashNIDValid, see Table B7.3.

### B13.10.13 Stash Group Identifier, StashGroupID

This field is used by a Requester to process different sets of StashOnceSep transactions by grouping them together and identifying each using StashGroupID.

Applicable only in the StashOnceSep request and StashDone response.