##### B4.2.2.2.2 Point of Persistence downstream of Home

If the PoP is downstream of the Home, for CleanSharedPersistSep:

- The Home must send the request downstream.
- The Subordinate Node must return a Comp response only after guaranteeing the request is accepted. A RetryAck response is not returned.
- When a Subordinate Node can guarantee all previous writes to the same address in a non-volatile memory are persistent, a Persist response must be returned to the Requester or the Home. The address location also contains the updated value even after the removal of power.

- The Home receives a Persist response from downstream. The Persist response is forwarded to the Requester:

    - The Subordinate is permitted, but not required, to return a combined CompPersist response to the Home.
    - The Home is permitted, but not required, to wait for the Persist response from the Subordinate. Permitting a Home to wait for a Persist response enables the Home to send a combined CompPersist response to the Requester instead of returning separate Comp and Persist responses.

- If the target is volatile memory, the Persist response can be given immediately. Such a situation must not return an error.

##### B4.2.2.2.3 Deep Persistent CMO

For high availability expectations, systems with non-volatile memory require guarantees that operation-critical data is preserved, even when the power and the back up battery fail simultaneously. The guarantee can be provided by a system by adding a mechanism to push previous writes to the PoDP. Deep Persistent CMO is supported by an attribute, called Deep, on PCMO transactions.

If the Completer of the request with Deep asserted does not support the Deep attribute, the Completer can ignore the attribute value and treat the request as having the Deep attribute deasserted. An error response must not be given to indicate that Deep persistence is not supported. See B13.10.19 Deep persistence, Deep.

#### B4.2.2.3 Dataless request attribute values

This section discusses the attribute values for Dataless requests across node interfaces.

See Chapter C1 Message Field Mappings for complete list.

Table B4.7 lists the values permitted for key attributes in Dataless requests from Request Node to Home Node.

Table B4.7: Request Node to Home Node Dataless request permitted attribute values

| Request     |   Size (bytes) | Excl   |   SnpAttr | MemAttr A C D E   |   Order | LikelyShared |   ExpCompAck |
|-------------|----------------|--------|-----------|-------------------|---------|--------------|--------------|
| CleanUnique |             64 | 0,1    |         1 | 0101 1101         |      00 |            0 |            1 |
| MakeUnique  |             64 | 0      |         1 | 0101 1101         |      00 |            0 |            1 |

Continued on next page