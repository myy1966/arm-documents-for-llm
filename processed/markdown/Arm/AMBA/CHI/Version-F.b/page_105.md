## B2.5 Transaction identifier field flows

This section shows the transaction identifier field flows for the different transaction types:

- B2.5.1 Read transactions
- B2.5.2 Dataless transactions
- B2.5.3 Write transactions
- B2.5.4 DVMOp transaction
- B2.5.5 Transaction requests with Retry
- B2.5.6 Protocol Credit Return transaction

In the associated figures:

- The fields included in each packet are:

    - For a Request packet: TgtID, SrcID, TxnID, StashNID, StashLPID, ReturnNID, ReturnTxnID, PGroupID, StashGroupID, and TagGroupID.
    - For a Response packet: TgtID, SrcID, TxnID, DBID, PGroupID, StashGroupID, and TagGroupID.
    - For a Data packet: TgtID, SrcID, TxnID, HomeNID, and DBID.
    - For a Snoop packet: SrcID, TxnID, FwdNID, FwdTxnID, and StashLPID.

- All fields with the same color are the same value.
- The curved loop-back arrows show how the Requester and Completer use fields from earlier packets to generate fields for subsequent packets.
- A box containing an asterix [*] indicates when a field is first generated, that is, indicating the agent that determines the original value of the field.
- A field enclosed in parentheses indicates that the value is effectively a fixed value. Typically this is the case for the SrcID field when a packet is sent, and the TgtID field when a packet arrives at its destination.
- A field that is crossed-out indicates that the field is not valid.
- It is permitted for the TgtID of the original transaction to be remapped by the interconnect to a new value. This is shown by a box containing the letter R. This is explained in more detail in Chapter B3 Network Layer.

> **_NOTE:_** An identifier field, in every packet sent, belongs to one of the following categories:
>
> - New value. An asterisk indicates that a new value is generated.
> - Generated from an earlier packet. A loop back arrow indicates the source.
> - Fixed value. The value is enclosed in brackets.
> - Not valid. The field is crossed-out.

In the following examples, any transaction identifiers that are not relevant for the example are sometimes omitted for clarity.

### B2.5.1 Read transactions

This section shows the identifier field flows in Read transactions with and without Direct Data Transfer:

- B2.5.1.1 ID value transfer with DMT
- B2.5.1.2 ID value transfer with DMT and separate Comp and Data
- B2.5.1.3 ID value transfer with DCT
- B2.5.1.4 ID value transfer without Direct Data Transfer