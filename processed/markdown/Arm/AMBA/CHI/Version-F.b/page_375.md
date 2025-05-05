## B10.3 Cache maintenance

This section describes additional Cache Maintenance Operations required in an RME-enabled system.

### B10.3.1 Cache Maintenance Operations

The additional Cache Maintenance Operations defined are:

- CleanInvalidPoPA
- WriteBackFullCleanInvPoPA
- WriteNoSnpFullCleanInvPoPA
- WriteNoSnpPtlCleanInvPoPA

The additional Cache Maintenance Operations provide support for the dynamic transition of memory granules between Physical Address Spaces.

To support the new Cache Maintenance Operations, a point in the system is defined, the Point of Physical Aliasing (PoPA). The PoPA is a point at which updates to a location in one PAS are visible to all other Physical Address Spaces. Cache Maintenance Operations could be required to more than one PAS to ensure that any data written earlier is fully visible to the intended Physical Address Spaces.

The RME\_Support property must be set to True to support the additional Cache Maintenance Operations at an interface. See B16.1.16 RME\_Support.

For further information, see PoPA and B4.2.2.1 Cache Maintenance transactions.

### B10.3.2 Remote invalidation

RME requires the ability to invalidate memory mapped as Non-shareable Cacheable remotely. The ability to remotely invalidate memory removes the need to rely on cache maintenance on each PE that may have memory mapped as Non-shareable Cacheable. To support this, the Nonshareable\_Cache\_Maint property must be set to True.

For further information, see B2.7.7 Mismatched Memory attributes and B16.1.17 Nonshareable\_Cache\_Maint.