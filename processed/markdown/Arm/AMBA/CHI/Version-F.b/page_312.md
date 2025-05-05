#### B6.3.1.1 MakeReadUnique(Excl)

When performing an Exclusive Store operation, MakeReadUnique(Excl) is the preferred alternative over the CleanUnique(Excl) request.

The permitted responses to the MakeReadUnique(Excl) request are included in Table B4.38 and Table B4.39.

##### B6.3.1.1.1 Result of an Exclusive access

The result of an Exclusive access is determined in the following manner:

- RespErr value of Exclusive Okay is not permitted in response to a MakeReadUnique(Excl).
- The Requester must use its local exclusive monitor along with the cache state in the response to determine the success of an Exclusive Store.

    - When the cache state in the response is Shared, the Requester must assume that the Exclusive access has failed.
    - When the cache state in the response is Unique, the Requester must use its own local monitor to determine the result of the Exclusive access.

##### B6.3.1.1.2 Home behavior

After checking the PoC monitor, if the Home determines the Exclusive Store passes, all other cached copies of the cache line must be invalidated. Subsequently, the Home sends a Comp response with the cache state of Unique to the Requester. The cache state can include [\_PD] if a cached copy in SD state was invalidated and the responsibility of writing back of the Dirty data is being passed to the Requester.

To avoid an Exclusive access livelock, the monitor must be capable of simultaneously tracking each individual LP Exclusive thread in the system.

A Home is permitted to use a precise Snoop Filter to determine the success or failure of an Exclusive access. If the Snoop Filter indicates that the Requester has lost the cache line, the Exclusive access is assumed to have failed.

In the absence of precise caching information from the Snoop Filter, the Home can use the SnpQuery snoop to determine the presence and state of the cache line at the Requester.

When a Home determines that an Exclusive Store transaction has failed, the following rules must be followed:

- If the Requester has lost the cache line, the Home is expected to send SnpPreferUniqueFwd or SnpPreferUnique to get a copy of the cache line. The Home is permitted to send SnpNotSharedDirty(Fwd), or SnpClean(Fwd), or SnpShared instead. The snoop must not be SnpSharedFwd nor any Invalidating snoop.
- The sender of the data is permitted to return, as appropriate, a UC or UD state in the response to the Requester if no other cached copies exist. The Completer must return data with SC state, if other copies exist. SD state is not permitted in the response to the Requester. This is because the Home cannot determine from the MakeReadUnique(Excl) request whether the Requester accepts data in SD state.

Data is provided in response to a MakeReadUnique(Excl) transaction when a cache line is lost to a snoop between the issuing of the MakeReadUnique(Excl) transaction and the point at which the Home actions the transaction or the Home cannot determine that the data has been retained.

### B6.3.2 System responsibilities

A system that implements the CHI protocol has the following responsibilities:

- Should include a monitor per LP for the efficient handling of Exclusive accesses.
- Must have a starvation prevention mechanism for all exclusive requests, whether using the monitor mechanism or some other means.