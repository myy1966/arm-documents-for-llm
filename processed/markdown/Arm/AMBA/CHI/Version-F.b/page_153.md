| Response        | Resp[2:0] | Cache line state when the response was sent | Action when a hidden copy of the cache line exists at Home | Notes                                                    |
|-----------------|-----------|---------------------------------------------|------------------------------------------------------------|----------------------------------------------------------|
| CompAck\_SD\_PD | 0b111     | SD                                          | Expose. This is expected, but not required.                | Responsibility for updating memory is passed to the Home |

- ᵃ A Unique copy can still exist at the Requester when the CopyBack Write transaction was a WriteClean.

If Home has kept a hidden copy of a cache line and later determines that no other copies of the line exist:

- If the hidden copy is Clean, the Home is expected, but not required, to expose that copy.
- If the hidden copy is Dirty, the Home is required to expose that copy.