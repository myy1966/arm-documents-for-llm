- Snooping by the Home Node, to determine if the Requester still holds a copy of the cache line.

### B6.2.4 Non-snoopable memory location

For a Non-snoopable memory location, a single monitor is used:

**System monitor**

The System monitor tracks Exclusive accesses to a Non-snoopable region. This monitor type is set by a ReadNoSnp(Excl) transaction and reset by an update to the location by another LP. System monitors can be placed at a PoS or at endpoint devices. Potentially, the number of devices in the system is much larger than the number of PoS and placing System monitors at a PoS can:

- Reduce System monitor duplication.
- Reduce the time taken for the system to detect failure of an Exclusive access.

A System monitor must be located to observe all transactions to the monitored location.