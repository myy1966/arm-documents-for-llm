- MemAttr values on a request received at Home must be preserved when the request is propagated to the Subordinate, except when the Subordinate is known to only have Normal memory. In this case, the MemAttr bit Device can be set to Normal.
- Order field must not be asserted:

    - A CMO intended for a particular address must not be sent to the interconnect before all previous transactions sent to the same address that can allocate the data in the Requester caches have completed.
    - A transaction intended for a particular address that can allocate data in Requester caches must not be sent to the interconnect before a previous CMO sent to the same address has completed.
    - A Completer is permitted, but not required, to wait for WriteData to send a Persist response. Examples of when a Completer can send an early Persist is when the Completer does not support Persistence on that memory location or the request encounters a Non-data Error (NDERR).

- A CMO is permitted, but not required, to be combined with a Write transaction to the same address when the write is ahead of the CMO. See B4.2.4 Combined Write requests.
- When Nonshareable\_Cache\_Maint property is True, a CMO must apply to locations marked in the page tables as Cacheable, irrespective of being marked Non-shareable or Shareable. The CMO must propagate to any cache that differentiates its entries based on Shareability.
- A CMO must:

    - Propagate to all caches that differentiate based on Cacheability.
    - A CMO must operate on any cache lines that have been cached with the same address and same PAS. A CMOis permitted, but not required, to operate on cache lines in a different PAS. The invalidation of a Dirty cache line in a different PAS must be ensured to be harmless.

- If a line is operated on by a:

    - CleanInvalid, CleanShared, or CleanSharedPersist: the line must propagate to an observable point by all agents that use the same PAS as the CMO.
    - CleanInvalidPoPA: the line must propagate to the observable PoPA by all agents in any PAS.
    - CleanSharedPersist: the line must propagate to the PoP.
    - CleanSharedPersist with Deep attribute set: the line must propagate to the Point of Deep Persistence (PoDP).

#### B4.2.2.2 Persistent CMO handling at Home

This section discusses the PoP at the Home and downstream of the Home. This section also introduces Deep attribute in Persistent CMO.

##### B4.2.2.2.1 Point of Persistence at Home

If the Home is the PoP, for CleanSharedPersistSep:

- The Home is permitted to not forward the CleanSharedPersistSep request to the Subordinate. When the Home decides not to forward the CleanSharedPersistSep request, a Persist response must be returned to the Requester.
- When the Home sends a Persist response, it is permitted, but not required, to combine the response with Comp and return a single CompPersist response to the Requester.