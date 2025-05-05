In WriteNoSnpDef:

- When DoDWT = 0, ReturnTxnID can take any value, and the value is not used in any response.
- When DoDWT = 1, the ReturnTxnID value is expected to be the original Requester TxnID but is permitted to be the Home TxnID. Used as the TxnID in the DBIDResp response.

In Combined Write:

- When DoDWT = 0, ReturnTxnID can take any value, and the value is not used in any response.
- When DoDWT = 1, the ReturnTxnID value is expected to be the original Requester TxnID but is permitted to be the Home TxnID. Used as the TxnID in the DBIDResp response.

### B2.4.5 Forward Transaction Identifier, FwdTxnID

A Snoop request from Home to RN-F also includes a FwdTxnID field to convey the value of TxnID in the Data response from the Snoopee. Its value must be the TxnID of the original Request.

The FwdTxnID field is only applicable in:

- SnpSharedFwd
- SnpCleanFwd
- SnpOnceFwd
- SnpNotSharedDirtyFwd
- SnpUniqueFwd
- SnpPreferUniqueFwd

The FwdTxnID field is inapplicable and must be set to 0 in all other snoops.

### B2.4.6 Data Identifier, DataID, and Critical Chunk Identifier, CCID

These fields identify the individual data packets within a transaction.

See B2.8.4 Data packetization and B2.8.6 Critical Chunk Identifier.

### B2.4.7 Logical Processor Identifier, LPID

This field is used when a single Requester contains more than one logically separate processing agent. The SrcID is used with LPID to uniquely identify the LP that generated the request.

The LPID must be set to the correct value for the following transactions:

- For any Non-snoopable Non-cacheable or Device access:

    - ReadNoSnp
    - WriteNoSnp
    - WriteNoSnpDef

- For Exclusive accesses, that can be one of the following transaction types:

    - ReadClean
    - ReadShared
    - ReadNotSharedDirty
    - ReadPreferUnique
    - MakeReadUnique
    - CleanUnique
    - ReadNoSnp
    - WriteNoSnp