## B8.4 DVM messages

This section provides additional information on the various DVM messages, their associated fields, and flit packing. It contains the following subsections:

- B8.4.1 DVM message payload
- B8.4.2 DVM message packing
- B8.4.3 TLB Invalidate
- B8.4.4 Branch Predictor Invalidate
- B8.4.5 Instruction Cache Invalidate
- B8.4.6 Synchronization

### B8.4.1 DVM message payload

The payload of a DVM operation from the Request Node to the Miscellaneous Node is distributed within:

- The Addr field in the DVM request from the Request Node.
- The lower 8 bytes of Data in the NonCopyBackWriteData packet.

The payload of a DVM operation from the Miscellaneous Node to the Request Node is distributed over two SnpDVMOp request packets using the Addr fields.

It is recommended, but not required, that the payload of a SnpDVMOp message matches the payload of the DVMOp message from which it originates.

Table B8.5 shows the various fields in the payload and their encodings.

Table B8.5: DVMOp fields and encodings

| Field    | Bits | Function                                                                                                             |
|----------|------|----------------------------------------------------------------------------------------------------------------------|
| AddrV    | 1    | Indicates if the message includes an address. </br> 0b0 No address included </br> Address included                   |
| VIV      | 2    | Virtual Index (VI) Valid. </br> 0b00 VI not valid </br> 0b01 Reserved </br> 0b10 Reserved </br> 0b11 VI is valid     |
| VMIDV    | 1    | 0b1 indicates that the Virtual Machine Identifer (VMID) is valid.                                                    |
| ASIDV    | 1    | 0b1 indicates that the Address Space Identifer (ASID) is valid.                                                      |
| Security | 2    | Indicates which Security state the invalidation applies to. </br> See Table B8.8 for the encodings for each DVMType. |

Continued on next page