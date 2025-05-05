- The DataPull request from the target Request Node is treated as a ReadNotSharedDirty Request.

See Chapter 7 Cache Stashing.

#### B4.2.2.1 Cache Maintenance transactions

A Cache Maintenance Operation (CMO) assists with software cache management. The protocol includes the following five transactions to support a Cache Maintenance Operation:

**CleanShared**

The completion response to a CleanShared request ensures that all cached copies are changed to a Non-dirty state and any Dirty copy is written back to memory.

**CleanSharedPersist**

The completion response to a CleanSharedPersist request ensures that all cached copies are changed to a Non-dirty state and any Dirty cached copy is written back to the Point of Persistence (PoP).

**CleanSharedPersistSep**

The Persist or combined CompPersist completion response to a CleanSharedPersistSep request ensures that all cached copies are changed to a Non-dirty state and any Dirty cached copy is written back to the PoP. Functionality of CleanSharedPersistSep is similar to CleanSharedPersist but allows two separate responses to the Requester.

When sending a PCMO, it is expected, but not required, that a Requester uses a CleanSharedPersistSep transaction instead of CleanSharedPersist.

Such a Requester must support receiving both separate Comp and Persist responses and a combined CompPersist response.

**CleanInvalid**

The completion response to a CleanInvalid request ensures that all cached copies are invalidated. The request requires that any cached Dirty copies must be written to memory.

**CleanInvalidPoPA**

The completion response to a CleanInvalidPoPA request ensures that all cached copies prior to the PoPA are invalidated. The request requires that any cached Dirty copies must be written past the PoPA. This enables writes to a location in one PAS to be visible to other Physical Address Spaces. Additional Cache Maintenance Operations could be required in the other Physical Address Spaces to ensure that any update is visible.

**MakeInvalid**

The completion response to a MakeInvalid request ensures that all cached copies are invalidated. The request permits that any cached Dirty copies are discarded.

The following characteristics are common to all six CMO transactions:

- The Resp field value in the Comp, indicating cache state, must be ignored by both the Requester and the Home.
- Sending of a CMO transaction to the interconnect from a Request Node and from the interconnect to a Subordinate Node is controlled by the BROADCASTPERSIST (BP) BROADCASTCACHEMAINT (BCM), and BROADCASTCMOPOPA interface signals. See B16.2 Optional interface broadcast signals.

> **_NOTE:_** Permitting Cache Maintenance Operations to be forwarded downstream of the Home Node incorporates system topologies where some observers could directly access locations downstream of the Home Node and software cache maintenance is required to make cached data visible to such observers.

- Cacheable and SnpAttr bit values must be observed.