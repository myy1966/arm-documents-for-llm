## B12.7 Atomic transactions

TagOp is applicable in Atomic transactions. The permitted values for the field are Invalid and Match.

The Physical Tags to be matched are provided in the write data and correspond to the valid data bytes in AtomicLoad, AtomicStore, and AtomicSwap. Only one set of tag bits are applicable in these Atomic transactions because the maximum data size is 8-byte. The remaining tag bits in the set are not applicable and must be set to 0.

In AtomicCompare with a data size of up to 16 bytes, the valid data still corresponds to only one set of tag bits.

In AtomicCompare with data size of 32-bytes the individual compare and swap data is only 16-bytes. Only one set of Physical Tag bits is required to be matched when TagOp is set to Match. Physical Tags must be duplicated to cover both Compare and Swap data. The Completer is permitted to use either set of Physical Tags to perform Tag Match.

The permitted TagOp values in the CompData response to Non-store Atomic transactions are Invalid and Transfer.

The Write data for Atomic transactions where TagOp is Invalid must have all TU bits and all the Tag bits set to 0.