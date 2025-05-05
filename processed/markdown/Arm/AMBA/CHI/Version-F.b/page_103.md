- SnpPreferUniqueFwd

The FwdNID field is inapplicable and must be set to 0 in all other snoops, except range-based Translation Lookaside Buffer Invalidate (TLBI) DVM operations. For range-based TLBI operations, the bits in the field are used for DVM payload.

### B2.4.13 Persistence Group Identifier, PGroupID

A CleanSharedPersistSep and Combined Write with Persistent CMO (PCMO) request includes a PGroupID to identify the Persistence Group that the request belongs to. If a Requester has persistent CMO requests from different functional agents that it would like to identify for performant persistent CMO handling, it can assign a different PGroupID value to each group of Persist requests. Use of this 8-bit field is applicable in CleanSharedPersistSep and Combined Write with PCMO transactions. It is also applicable in Persist and CompPersist responses. It is inapplicable and must be set to zero in all other requests and responses. See B13.10.8 Persistence Group Identifier, PGroupID :

- PGroupID must be sent in the CleanSharedPersistSep request and a Combined Write request that includes a PCMO.
- The PGroupID value returned in the Persist response can be used by a Requester to separately track completions of Persist responses from each group.
- It is expected that a Requester that does not support multiple persistence groups sets the PGroupID value to 0.
- Typically, a Requester that is making use of PGroupID for passing a barrier does not reuse a PGroupID value until all the earlier sent CleanSharedPersistSep requests from that group have received Persist responses.
- The Completer is required to reflect back PGroupID in the Persist and CompPersist responses, and the responses of Combined Write requests that include a PCMO.
- The PGroupID field in the Comp and CompCMO response from both the Home and Subordinate is inapplicable and must be set to 0.

### B2.4.14 Stash Group Identifier, StashGroupID

To identify the Stash Group that the request belongs to, a StashOnceSep request includes a StashGroupID. The same StashGroupID value from the request is later used by a StashDone response in the transaction flow. If a Requester has StashOnceSep requests from different functional agents that can be identified for performant stash handling, a different StashGroupID value to each group of Stash requests can be assigned.

Use of this 8-bit field is applicable in the StashOnceSep request and StashDone response. StashGroupID is inapplicable and must be set to 0 in all other requests and responses.

- StashGroupID must be sent in the StashOnceSep request.
- The StashGroupID value returned in the StashDone response can be used by a Requester to separately track completions of Stash transactions from each group.
- It is expected that a Requester that does not support multiple stash groups sets the StashGroupID value to 0.
- The Completer is required to reflect back StashGroupID in the StashDone response.

See B13.10.13 Stash Group Identifier, StashGroupID.

### B2.4.15 Tag Group Identifier, TagGroupID

To identify the Tag group that the request belongs to, a Write request where TagOp is set to Match includes a TagGroupID. The same TagGroupID value from the request is later used by a TagMatch response in the transaction flow to notify the Requester if the TagMatch operation passed or failed.