***ASID* field**

The ASID field contains an 8-bit or 16-bit Address Space Identifier.

- Armv7 supports an 8-bit ASID.
- From Armv8, an 8-bit and 16-bit ASID are supported.

It cannot be determined from a DVM message whether the message uses an 8-bit or 16-bit ASID.

All 8-bit ASID messages are required to set the ASID[15:8] bits to zero.

It is expected that most systems will use a single ASID size across the entire system, either 8-bit ASID or 16-bit ASID.

In a system that contains a mix of 8-bit ASID and 16-bit ASID components, it is expected that all maintenance is done by an agent that uses 16-bit ASID. This ensures that the agent can perform maintenance on both the 8-bit ASID and 16-bit ASID components.

The interoperability requirements include:

- For an 8-bit ASID agent sending a message to a 16-bit ASID agent, a message appears as a 16-bit ASID with the upper 8 bits set to zero.
- For a 16-bit ASID agent sending a message to an 8-bit VMID agent:

    - If the upper 8 bits are zero, the message was received correctly.
    - If the upper 8 bits are non-zero, over-invalidation occurs as the 8-bit ASID agent ignores the upper 8 bits.

***VMID* field**

The VMID field contains an 8-bit or 16-bit Virtual Machine Identifier.

- Armv7 and Armv8 support an 8-bit VMID.
- From Armv8.1, an 8-bit and 16-bit VMID are supported.

It cannot be determined from a DVM message whether the message uses an 8-bit or 16-bit VMID.

All 8-bit VMID messages are required to set the VMID[15:8] field to zero.

It is expected that most systems use a single VMID size across the entire system, either 8-bit VMID or 16-bit VMID.

In a system that contains both 8-bit VMID and 16-bit VMID components, it is expected that all maintenance is done by an agent that uses 16-bit VMID. This ensures that the agent can perform maintenance on both the 8-bit VMID and 16-bit VMID components.

The interoperability requirements include:

- For an 8-bit VMID agent sending a message to a 16-bit VMID agent, a message appears as a 16-bit VMID with the upper 8 bits set to zero.
- For a 16-bit VMID agent sending a message to an 8-bit VMID agent:

    - If the upper 8 bits are zero, the message was received correctly.
    - If the upper 8 bits are non-zero, over-invalidation occurs as the 8-bit VMID agent ignores the upper 8 bits.

From Armv8.1, VMIDExt is used to transport the upper byte of 16-bit VMIDs.