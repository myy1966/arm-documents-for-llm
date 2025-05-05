## B11.7 Trace Tag

A TraceTag bit per channel provides enhanced support for debugging, tracing, and performance measurement of systems.

### B11.7.1 TraceTag usage and rules

The rules for when to set and how to propagate TraceTag bit values are:

- The TraceTag bit can be set by the transaction initiator or an interconnect component.
- A component that receives a packet with the TraceTag bit set in every received packet must preserve and reflect the value back in any response packet or spawned packet generated in response to the received packet. Otherwise, the TraceTag bit in the response and spawned packet can take any value. This requirement is true only when the TraceTag bit in the response packet is applicable. Examples of pairs of such response and received packets are CompAck in response to multiple CompData packets and Snoop response to the pair of two DVMOp packets.
- If a received packet spawns multiple responses, such as a Write request resulting in separate Comp and DBIDResp responses, or a Read request generating separate DataSepResp and RespSepData responses, all such spawned responses are required to have the TraceTag bit set if the spawning packet has the TraceTag bit set. If the spawning packet does not have the TraceTag bit set, the value of the TraceTag bit in a spawned packet is independent of the value of the bit in other related spawned packets.
- If a component can receive multiple packets that are associated with a single transaction, then for each packet that it, in turn, generates, the TraceTag value is only required to be set if it is set in the associated received packet. For example:

    - A Write transaction flow at the Request Node could have write data and CompAck as two responses for received packets DBIDResp and Comp respectively. As CompAck is in response to the received Comp only, its TraceTag bit value is only required to depend on the TraceTag bit value in the Comp packet and similarly for the write data and DBIDResp Response-Received Packet pair. A request that receives separate DataSepResp and RespSepData responses and generates a CompAck, is only required to have the TraceTag bit set in CompAck if RespSepData has the TraceTag bit set.
    - The TraceTag bit in the NonCopyBackWriteDataCompAck response from the Request Node must be set if either one of Comp or DBIDResp that caused the WriteData response have the TraceTag bit set.

- When an interconnect receives a packet with the TraceTag bit set, the value must be preserved and not reset the value.

> **_NOTE:_** Propagating the value of the TraceTag bit on a resulting cache eviction is IMPLEMENTATION DEFINED.
>
> The precise mechanism to trigger and utilize the TraceTag bit is IMPLEMENTATION DEFINED.
>
> It is expected that the TraceTag bit is limited to single system-wide use at any time.
>
> Some of the ways the trace tag mechanism can be used are:
>
> - Debug, by tracing transaction flows through the system.
> - Performance counting
> - Latency measurement
>
> Examples, not an exhaustive list, of Request-Response pairs are:
>
> - A Snoop response, with or without data, in response to a Snoop request.