## B4.6 Silent cache state transitions

A cache can change state due to an internal event without notifying the rest of the system.

The legal silent cache state transitions are shown in Table B4.35 and Table B4.36. In some cases it is possible, but not required, to issue a transaction to indicate that the transition has occurred. If such a transaction is issued, then the cache state transition is visible to the interconnect and is not classified as a silent transition.

The RN-F action described in Table B4.35 as Local sharing, describes the case where an RN-F specifies a Unique cache line as Shared, effectively disregarding the fact that the cache line remains Unique to the RN-F. For example, this can happen when the RN-F contains multiple internal agents and the cache line becomes shared between them.

For silent cache state transitions:

- Cache eviction and Local sharing transitions can occur at any point and are IMPLEMENTATION DEFINED.
- Store and Cache Invalidate transitions can only occur as the result a deliberate action, which in the case of a core is caused by the execution of a particular program instruction.
- A cache state change from UC to UCE is not permitted.

Table B4.35 indicates how a silent cache state transition can be made non-silent at the interface.

Table B4.35: Legal silent cache state transitions and how they can be made non-silent

| RN-F action      | Present RN-F state | Next RN-F state | Transaction that can be used to make the action non-silent |
|------------------|--------------------|-----------------|------------------------------------------------------------|
| Cache eviction   | UC                 | I               | Evict, WriteEvictFull, or WriteEvictOrEvict                |
| Cache eviction   | UCE                | I               | Evict                                                      |
| Cache eviction   | SC                 | I               | Evict or WriteEvictOrEvict                                 |
| Local sharing    | UC                 | SC              | -                                                          |
| Local sharing    | UD                 | SD              | -                                                          |
| Cache Invalidate | UD                 | I               | Evict                                                      |
| Cache Invalidate | UDP                | I               | Evict                                                      |

Table B4.36 indicates how a silent cache state transition can occur within the RN-F, depending on different types of stores.

Table B4.36: Legal silent cache state transitions resulting from internal RN-F stores

| RN-F action | Present RN-F state | Next RN-F state | A result of                      |
|-------------|--------------------|-----------------|----------------------------------|
| Store       | UC                 | UD              | Full or partial cache line store |
| Store       | UCE                | UDP             | Partial cache line store         |
| Store       |                    | UD              | Full cache line store            |
| Store       | UDP                | UD              | Store that fills the cache line  |