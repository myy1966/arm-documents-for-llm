### B8.2.3 Flow control

This section describes the flow requirements for DVMOp and SnpDVMOp.

#### B8.2.3.1 DVMOp

The flow requirements for a DVMOp include:

- A DVMOp can receive a RetryAck response from a Miscellaneous Node.

    - A DVMOp that receives a RetryAck response must wait for a PCrdGrant response from the Miscellaneous Node that has the appropriate PCrdType.

- All previous DVMOp requests whose completion needs to be guaranteed by the DVMOp(Sync) must have received a Comp response before the Request Node can send the DVMOp(Sync).
- For DVMOp(Non-sync) operations, the interconnect must guarantee forward progress. This requires that there should be at least one tracker entry in the Miscellaneous Node reserved for DVMOp(Non-Sync).
- It is permitted to overlap a DVMOp(Non-sync) and a DVMOp(Sync) from the same Request Node, if the DVMOp(Sync) is not required to guarantee completion of the DMVOp(Non-sync).

#### B8.2.3.2 SnpDVMOp

The flow requirements for a SnpDVMOp include:

- Each SnpDVMOp transaction requires two SnpDVMOp request packets.

    - Both SnpDVMOp request packets corresponding to a single transaction must use the same TxnID.
    - The two SnpDVMOp request packets corresponding to a single transaction can be sent or received in any order.
    - To prevent deadlocks, due to the two-part SnpDVMOp requests that use the Snoop channel, a SnpDVMOp transaction must only be sent when the receiving Request Node has pre-allocated resources to accept both parts of the SnpDVMOp transaction.
    - A Request Node must provide a response to a SnpDVMOp transaction only after both SnpDVMOp request packets are received corresponding to that transaction.
    - A Request Node must provide a response to a SnpDVMOp only when a further SnpDVMOp from a Miscellaneous Node can be accepted.

- Each RN-F and RN-D in the system specifies the number of SnpDVMOp transactions it can accept concurrently.

    - Each RN-F and RN-D in the system must be able to accept at least one SnpDVMOp(Non-Sync) transaction in addition to a SnpDVMOp(Sync) transaction.
    - The minimum number of SnpDVMOp transactions that must be accepted concurrently is two. This is the default number for Request Nodes that do not specify a number.

- A SnpDVMOp(Sync) operation at a Request Node that has issued a StashOnceSep request must wait until all outstanding StashDone responses are received for StashOnceSep requests that use invalidated page entries.

For SnpDVMOp(Non-sync):

- Multiple SnpDVMOp(Non-sync) transactions can be outstanding from a Miscellaneous Node.

For SnpDVMOp(Sync):

- Only one SnpDVMOp(Sync) can be outstanding from a Miscellaneous Node to a Request Node.
- When responding to a SnpDVMOp(Sync), a Request Node can depend on the forward progress of any transaction, except for the completion of an outstanding DVMOp(Sync) request.