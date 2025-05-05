- WriteNoSnpZero
- WriteUnique
- WriteUnique*CMO
- WriteUniqueZero
- Atomic

When a ReadNoSnp or ReadOnce* transaction requires Request Order or Endpoint Order:

- The Requester requires a ReadReceipt to determine when it can send the next ordered request.
- At the Completer a ReadReceipt means the request has reached the next ordering point that maintains requests in the order they were received:

    - Requests that require Request Order maintain order between requests to the same address from the same source.
    - Requests that require Endpoint Order maintain order between requests to the same endpoint address range from the same source.

- A Completer that is capable of sending separate Non-data and Data-only responses can send RespSepData response instead of ReadReceipt and achieve the same functional behavior.

When a WriteNoSnp, WriteNoSnpDef, WriteNoSnpZero, or a Non-snoopable Atomic transaction requires Request Order or Endpoint Order:

- The Requester requires a DBIDResp or DBIDRespOrd to determine when sending the next ordered request.
- The Completer sending a DBIDResp or DBIDRespOrd response means that a data buffer is available, and that the Write request has reached a PoS that maintains requests in the order they were received:

    - For requests that require Request Order, the Completer maintains order between requests to the same address from the same source.
    - For requests that require Endpoint Order, the Completer maintains order between requests to the same endpoint address range from the same source.

When a WriteUnique transaction without ExpCompAck asserted, or a WriteUniqueZero or a Snoopable Atomic transaction require Request Order:

- The Requester requires a DBIDResp or DBIDRespOrd to determine when sending the next ordered request.
- The Completer sending a DBIDResp or DBIDRespOrd response means that maintains order between requests to the same address from the same source.

Additionally, when a Completer sends DBIDRespOrd for a request with a no order or Request Order requirement, the Completer guarantees to order all subsequent no order or Request Order received requests to the same address from the same source against this request, where these later received requests are of any transaction type, not necessarily Write transactions. When the write includes a CMO, the order is guaranteed against both the write and the CMO.

When a WriteUnique, WriteNoSnp, or one of their Combined Write variants requires OWO:

- CompAck is required. The Request Node must assert ExpCompAck.
- The Request Node requires a DBIDResp or DBIDRespOrd.
- The Completer is a PoS. A PoS sending DBIDResp or DBIDRespOrd means:

    - A data buffer is available.
    - The PoS guarantees that the completion of the coherence action on this write does not depend on completion of the coherence action on a subsequent write that requires OWO.
    - The write is not made visible until CompAck is received.