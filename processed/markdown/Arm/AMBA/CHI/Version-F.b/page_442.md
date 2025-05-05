Applicable in Forward-type snoops.

Inapplicable and must be 0 in all other Snoop requests, except range-based TLBI DVM operations.

In range-based TLBI DVM operations, the bits in the field are used for DVM payload.

### B13.10.7 Logical Processor Identifier, LPID

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

See Chapter B6 Exclusive accesses for further details.

In requests, when applicable, the same bits in the packet are used for TagGroupID, PGroupID, and StashGroupID.

For other transactions, the LPID value is permitted, but not required, to indicate the original LP that caused a transaction to be issued.

### B13.10.8 Persistence Group Identifier, PGroupID

This field is used by a Requester to process different sets of CleanSharedPersistSep transactions by grouping them together and identifying each using PGroupID.

Applicable in the CleanSharedPersistSep and Write*CleanShPerSep requests and the Persist and CompPersist responses.

Inapplicable and must be set to 0 in all other requests and responses.

In requests, when applicable, the same bits in the packet are used for LPID, TagGroupID, and StashGroupID.

In responses, when applicable, the same bits in the packet are used for DBID, TagGroupID, and StashGroupID.

### B13.10.9 Stash Node Identifier, StashNID

This field identifies the target of the Stash request. Provides a valid stash target value when the corresponding StashNIDValid bit is asserted. See B7.4 Stash target identifiers.

Applicable in Stash requests.

Inapplicable and must be 0 for all other requests. For ReadNoSnp and ReadNoSnpSep requests, the same bits in the packet are used for ReturnNID.