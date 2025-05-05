**Advanced Microcontroller Bus Architecture, AMBA**

The AMBA family of protocol specifications is the Arm open standard for on-chip buses. AMBA provides solutions for the interconnection and management of functional blocks that make up a System-on-Chip (SoC). Applications include the development of embedded systems with one or more processors or signal processors and multiple peripherals.

**Aligned**

A data item stored at an address that is divisible by the highest power of 2 that divides into its size in bytes. Aligned halfwords, words and doublewords therefore have addresses that are divisible by 2, 4 and 8 respectively.

An aligned access is one where the address of the access is aligned to the size of each element of the access.

**AMBA**

See Advanced Microcontroller Bus Architecture.

**At approximately the same time**

Two events occur at approximately the same time if a remote observer might not be able to determine the order in which they occurred.

**Barrier**

An operation that forces a defined ordering of other actions.

**Blocking**

Describes an operation that prevents following actions from continuing until the operation completes.

A non-blocking operation can permit following operations to continue before it completes.

**Byte**

An 8-bit data item.

**Cache**

Any cache, buffer, or other storage structure in a caching Manager that can hold a copy of the data value for a particular address location.

**Cache hierarchy**

The organisation of different size caches in a hierarchy, typically within the cache with faster access and smaller size closer to the core and larger and slower access ones farther away from the core. The last level of this hierarchy might be conncted to the memory. In this specification, in relation to a referenced cache, above refers to caches closer to the core, and below refers to caches farther from the core.

**Cache line**

The basic unit of storage in a cache. Its size in words is always a power of two. A cache line must be aligned to the size of the cache line.

The size of the cache line is equivalent to the coherency granule.

**Cache state**

State of a block of data in a cache, of 64-byte size in this specification. The state determines if the block is cached in any other caches in the system and also if it is different from the copy of the block in memory. See B1.5.2 Cache state model for a description of the cache states supported in this specification.

**ceil()**

A function that returns the lowest integer value that is equal to or greater than the input to the function.

**Channel**
