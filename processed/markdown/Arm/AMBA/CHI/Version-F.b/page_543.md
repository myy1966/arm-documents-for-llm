The action of a Requester component reading the value held at a particular address location. For a processor, a load occurs as the result of executing a particular instruction. Whether the load results in the Requester issuing a read transaction depends on whether the accessed cache line is held in the local cache.

See also Speculative read, Store.

**Main memory**

The memory that holds the data value of an address location when no cached copies of that location exist. For any location, main memory can be out of date with respect to the cached copies of the location, but main memory is updated with the most recent data value when no cached copies exist.

Main memory can be referred to as memory when the context makes the intended meaning clear.

**Memory Management Unit (MMU)**

Provides detailed control of the part of a memory system that provides address translation. Most of the control is provided using translation tables that are held in memory, and define the attributes of different regions of the physical memory map.

See also System Memory Management Unit (SMMU).

**Memory Subordinate component**

A Memory Subordinate component, or Memory Subordinate, is a Subordinate component with the following properties:

- A read of a byte from a Memory Subordinate returns the last value written to that byte location.
- A write to a byte location in a Memory Subordinate updates the value at that location to a new value that is obtained by subsequent reads.
- Reading a location multiple times has no side-effects on any other byte location.
- Reading or writing one byte location has no side-effects on any other byte location.

See also Component, Requester component, Peripheral Subordinate component.

**Message**

See Message.

**Observer**

A processor or other Requester component, such as a peripheral device, that can generate reads from or writes to memory.

**Outstanding request**

A transaction is outstanding from the cycle that the request is first issued until either:

- The transaction is fully completed, as determined by the return of all responses that are expected for the transaction.
- It receives RetryAck and PCrdGrant, and is either:

    - Retried using a credit of the appropriate PCrdType, and then is fully completed as determined above.
    - Canceled, and returns the received credit using the PCrdReturn message.

**Packet**

See Packet.

**Page-based Hardware Attributes (PBHA)**
