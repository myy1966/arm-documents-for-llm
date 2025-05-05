## B16.2 Optional interface broadcast signals

This specification includes optional pins to determine broadcasting of certain groups of transactions in the interconnect. These pins are optional at the Request Node to the interconnect, and the interconnect to the Subordinate Node interfaces. The optional broadcast pins are:

- B16.2.1 BROADCASTINNER and BROADCASTOUTER
- B16.2.2 BROADCASTCACHEMAINT
- B16.2.3 BROADCASTPERSIST
- B16.2.4 BROADCASTATOMIC
- B16.2.5 BROADCASTICINVAL
- B16.2.6 BROADCASTMTE
- B16.2.7 BROADCASTERTLBIINNER and BROADCASTTLBIOUTER
- B16.2.8 BROADCASTCMOPOPA

An implementation that includes these signals at the interface must ensure that the signal values are stable when Reset is deasserted.

### B16.2.1 BROADCASTINNER and BROADCASTOUTER

The **BROADCASTINNER** and **BROADCASTOUTER** signals are used to control the issuing of Snoopable transactions from an interface. It is required that these two pins must be set to the same value.

When the signals are present and deasserted, all transactions are converted to Non-snoopable equivalents before they are sent. The transaction conversion from Snoopable to Non-snoopable, using the **BROADCASTINNER** and **BROADCASTOUTER** signals, the following conversions apply:

- All Read transactions must be converted to ReadNoSnp.
- All Snoopable CMO transactions must be converted to Non-snoopable CMO.
- The following Dataless transactions must be dropped:

    - CleanUnique
    - MakeUnique
    - Evict
    - StashOnce
    - StashOnce*Unique
    - StashOnce*Shared

- All Combined Writes must be converted to Combined WriteNoSnp.
- All Write transactions, except WriteEvictFull and WriteEvictOrEvict, must be converted to WriteNoSnp.
- WriteEvictFull and WriteEvictOrEvict transactions must be dropped.
- All Snoopable Atomic transactions must be converted to Non-snoopable.
- PrefetchTgt transaction conversion is not required.

### B16.2.2 BROADCASTCACHEMAINT

The **BROADCASTCACHEMAINT** signal is used to control the issuing of Cache Maintenance Operations when there are software-managed caches downstream of the interface.

When the **BROADCASTCACHEMAINT**, **BROADCASTINNER**, and **BROADCASTOUTER** signals are all present and deasserted:

- CleanShared, CleanInvalid, and MakeInvalid transactions are not issued.