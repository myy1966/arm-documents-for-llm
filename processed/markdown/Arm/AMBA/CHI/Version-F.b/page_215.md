## B4.4 Request transactions and corresponding Snoop requests

For a required coherency action, a Home can select from a choice of multiple permitted snoop types. This section describes examples of how a Home selects the snoop to send and the amount of snoops to send.

While responding to a Request, the selection of which snoop to use is determined from the intended outcome, that is the desired final state of the cache line at the Requester and the required or desired cache state at the Snoopee.

See B4.2 Request types for required cache state at peer Request Nodes. See B4.8 Cache state transitions at a Snoopee for details of Snoopee cache state transitions.

### B4.4.1 Number of snoops to send

The Home Node can send Non-forwarding Snoops to more than one RN-F, including to all RN-Fs.

The Home Node is only permitted to send a Forwarding Snoop to one RN-F.

In the case of an invalidation, the invalidating snoop must be sent at least to all the other cached copies. Whereas for a Non-invalidating snoop, the Home Node is:

- Permitted, but not required, to send the snoop to all RN-Fs with the cached copies.
- Must be able to obtain a copy of the Dirty line. In the case of a Unique Dirty cache line state, the Home Node must send a snoop to the RN-F with the Unique Dirty cached copy.

For Write transactions with stash hint, the Home Node must also send invalidating snoops to all Non-stash target RN-Fs that have a copy of the cache line:

- For WriteUniqueFullStash, the expected snoop to Non-stash target nodes is SnpMakeInvalid.
- For WriteUniquePtlStash, the expected snoop to Non-stash target nodes is SnpCleanInvalid.

A snoop filter or directory can be included within the interconnect to support filtering of snoops.

### B4.4.2 Selection of snoop to send

A Home Node, based on internal preferences and implementation constraints, might prefer one of the expected snoops or substitute an expected snoop with others. See Table B4.25 for the expected snoop per Request type.

Table B4.25 shows the snoops expected to be used by the Home Node for a given Request. A Home is permitted to substitute the expected snoop with another snoop that accomplishes the required Snoopee state transition.

Table B4.25: Expected Snoop requests per Request from a Request Node

| Request category | Request              | Expected Snoop                             |
|------------------|----------------------|--------------------------------------------|
| Read             | ReadNoSnp            | None or SnpOnceFwd ᵃ                       |
| Read             | ReadNoSnpSep         | n/a                                        |
| Read             | ReadOnce             | SnpOnceFwd ᵃ                               |
| Read             | ReadOnceCleanInvalid | SnpUnique or SnpOnceFwd ᵃ                  |
| Read             | ReadOnceMakeInvalid  | SnpUnique, SnpUniqueFwd ᵃ, or SnpOnceFwd ᵃ |
| Read             | ReadClean            | SnpCleanFwd                                |
| Read             | ReadNotSharedDirty   | SnpNotSharedDirtyFwd                       |

Continued on next page