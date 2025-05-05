#### B4.7.1.1 MakeReadUnique transaction

This section describes the permitted responses and the cache state transitions at the Requester, for the MakeReadUnique and MakeReadUnique(Excl) transactions. The additional MakeReadUnique(Excl) behavioral requirements are described in B6.3.1.1 MakeReadUnique(Excl).

##### B4.7.1.1.1 Permitted responses

Table B4.38 shows the permitted responses in a MakeReadUnique transaction. Table B4.39 shows the additional responses that are permitted only when the Exclusive bit in the request is set to one. This attribute is indicated by adding the suffix (Excl) to the request.

Some key features of the permitted responses are:

- A response without data, Comp\_UD\_PD, indicates that the Requester is being passed responsibility for a Dirty cache line. This can occur when the Requester holds a SharedClean copy of the cache line and another agent holds a SharedDirty copy. The Home invalidates the SharedDirty copy, for example using a SnpMakeInvalid transaction, and subsequently passes the responsibility for the Dirty cache line to the Requester that issued the MakeReadUnique transaction.
- A response with a cache state of SC is only permitted in response to an Exclusive version of MakeReadUnique. Comp\_SC, an example of a response with a cache state of SC, is sent when the Home determines that the Exclusive Store has failed but the snoop filter, or response to a SnpQuery snoop to the Requester, indicates that the Requester still holds a copy of the cache line while there is another shared copy in the system.

> **_NOTE:_** The above situation can occur with a non-full address PoC exclusive monitor. The monitor bit for an LP can be reset by another LP performing an Exclusive store to a different address location. This store to a different address does not invalidate the cached copy of the address location being used for Exclusive access by the first Requester.

Table B4.38 shows the permitted responses in both the non-Exclusive and Exclusive MakeReadUnique transaction.

Table B4.38: Permitted responses in the MakeReadUnique transaction

| Response received | Cache line state                       | Action                                                                                                                 |
|-------------------|----------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Comp\_UC          | Can be Clean or Dirty at the Requester | Requester retains its copy of the cache line All other cached copies have been invalidated.                            |
| Comp\_UD\_PD      | Must become Dirty at the Requester     | Requester retains its copy of the cache line. Dirty copy of the cache line held elsewhere has been invalidated.        |
| CompData\_UC      | Clean copy is given to the Requester   | Requester lost the cache line while the transaction was in progress. Combined data and completion responses are given. |
| CompData\_UD\_PD  | Dirty copy is given to the Requester   | Requester lost the cache line while the transaction was in progress. Combined data and completion responses are given. |

Continued on next page