A component that receives transactions and responds to them.

It is possible that a single component can act as both a Subordinate component and as a Manager component. For example, a Direct Memory Access (DMA) component can be a Subordinate component when it is being programmed and a Manager component when it is initiating transactions to move data.

See also Requester component, Memory Subordinate component, Peripheral Subordinate component.

**Synchronization barrier**

See Barrier.

**System Memory Management Unit (SMMU)**

A system-level MMU. That is, a system component that provides address translation from a one address space to another. An SMMU provides one or more of:

- Virtual Address (VA) to Physical Address (PA) translation
- VA to Intermediate Physical Address (IPA) translation
- IPA to PA translation.

See also Memory Management Unit (MMU).


**TLB**

See Translation Lookaside Buffer (TLB).

**Transaction**

See Transaction.

**Translation Lookaside Buffer (TLB)**

A memory structure containing the results of translation table walks. TLBs help to reduce the average cost of a memory access.

See also System Memory Management Unit (SMMU), Translation table, Translation table walk.

**Translation table**

A table held in memory that defines the properties of memory areas of various sizes from 1KB.

See also Translation Lookaside Buffer (TLB), Translation table walk.

**Translation table walk**

The process of doing a full translation table lookup.

See also Translation Lookaside Buffer (TLB), Translation table.

**Unaligned**

An unaligned access is an access where the address of the access is not aligned to the size of an element of the access.

**Unaligned memory accesses**

Are memory accesses that are not, or might not be, appropriately halfword-aligned, word-aligned, or doubleword-aligned.

**UNPREDICTABLE**

In the AMBA Architecture, it means that the behavior cannot be relied upon.

UNPREDICTABLE behavior must not be documented or promoted as having a defined effect.

When UNPREDICTABLE appears in body text, it is always in small capitals.

**Upstream**