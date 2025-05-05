> **_NOTE:_** Interface parity optionally extends the error detection provided on the DAT channel by the DataCheck field.
>
> The Data\_Check and Check\_Type properties are used to indicate if DataCheck is supported in the DAT packet.

### B9.2.3 Interoperability of Poison and DataCheck

If the recipient of a Data packet does not support the Poison and DataCheck features, the interconnect must enumerate and convert, as necessary, the Poison and DataCheck error responses to a DERR in the DAT packet.

If support for the Poison and DataCheck features is not similar across an interface, the following rules apply:

- Poison must be mapped to DataCheck or DERR if Poison is not supported across the interface. At such an interface, Poison is expected but not required to be mapped to DataCheck instead of DERR, if DataCheck is supported. When converting from Poison to DataCheck, when an 8-byte chunk is marked as Poisoned, all 8 bits of DataCheck corresponding to that chunk must be manipulated to generate a parity error.
- DataCheck must be mapped to Poison or DERR if DataCheck is not supported across the interface. At such an interface, DataCheck is expected but not required to be mapped to Poison instead of DERR, if Poison is supported. When converting from DataCheck to Poison, if one or more DataCheck bits in a given 8-byte chunk generates a parity error, the Poison bit corresponding to that chunk must be set.

> **_NOTE:_** The difference between the handling of Poison and DERR is that a Poison error in a received data packet is typically deferred by the receiver, but a DERR error is typically not deferred by the receiver.

It is sufficient for the Sender of a data packet that detects a Poison error to indicate this in the Poison bits. It is not a requirement that the Sender sets the RespErr field value to DERR.

It is sufficient for the Sender of a data packet that detects a DataCheck error to indicate this in the DataCheck field and is not required to set RespErr field value to DERR.

As Poison and DataCheck fields are independently set, one type of error does not require setting of the other.

In a Data packet that has the RespErr field value set to DERR or NDERR, the value of the Poison and DataCheck fields are inapplicable and can take any value.