    - The Requester is permitted to treat SnpPreferUnique and SnpPreferUniqueFwd as either invalidating or non-invalidating. The Home can determine how these snoops are treated by the Snoopee by inspecting the Snoop response.
    - All other snoops are non-invalidating and the Requester is required to keep a copy of the cache line.

If the Home does not have an SF, or the SF is imprecise, and the Home cannot determine if the Requester still has a copy of the cache line at the point that the transaction completes, the Home must assume the cache line is lost at the Requester and provide data with the response.

A Requester that receives a response with data, while still holding the line in SD state, must use its own copy of the cache line, rather than the copy returned with the response.

> **_NOTE:_** A Requester that receives a response with data, while still holding the line in SD state implies there is no snoop filter present or that the snoop filter is imprecise. In this case, the data could be returned with the response is Stale.

If the Requester is aware that there is no snoop filter, a CleanUnique transaction can be used instead of MakeReadUnique to avoid an unnecessary memory read when the cache line is not cached at any other agent.

> **_NOTE:_** Use of the CleanUnique transaction can avoid an unnecessary memory read in the absence of a snoop filter. The unnecessary memory read occurs when the cache line remains cached at the Requester, but a snoop filter is not present in the system or a SnpQuery snoop is not used and a cached copy is not available from another agent in the system. However, using a CleanUnique transaction results in the Requester needing to issue another transaction in the case where the cache line is lost due to a snoop while the transaction is in progress.

Table B4.38 shows the state transitions and responses that are applicable to both non-Exclusive and Exclusive versions of MakeReadUnique. Table B4.41 shows the additional state transitions and responses that apply only to the Exclusive version of the request.

The response rules are:

- The cache state in the response to a non-Exclusive MakeReadUnique must be Unique.
- The cache state in the response to an Exclusive MakeReadUnique is permitted to be Unique or Shared.
- The cache state in the response to an Exclusive and to a Non-exclusive MakeReadUnique must not include Shared Dirty.
- For each permitted combined completion and data response, a corresponding response with separate completion and data is permitted.

Table B4.40 and Table B4.41 include columns for:

- The initial cache state.
- The cache state immediately before the transaction response is received.
- An indication of Home sending the original Requester an invalidating snoop after the Requester has issued the MakeReadUnique request.
- The final state for each of the possible response combinations.

The handling of a MakeReadUnique transaction at the Home depends on the availability or not of a precise Snoop Filter. Table B4.40 and Table B4.41 also include the responses that are permitted with and without a precise Snoop Filter:

- The table column labeled: Snoop Filter - Precise, covers the cases when the precise state of the cache line at the Requester, at the response time, is known. The Home obtains the knowledge of precise state from a snoop filter, or by sending a SnpQuery snoop, or in some other IMPLEMENTATION DEFINED manner.