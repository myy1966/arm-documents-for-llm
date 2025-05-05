    > **_NOTE:_** Both parts of the message must carry the same TxnID. The Request Node must have resources available to accept the SnpDVMOp. See B8.2.3 Flow control.

5. After completing the required actions, each recipient of the SnpDVMOp sends a single SnpResp response to the Miscellaneous Node.

    > **_NOTE:_** Sending of a SnpResp implies that the target Request Node has forwarded the SnpDVMOp to the required Request Node structures and has freed up the resources needed to accept another DVM operation. Sending of a SnpResp does not imply that the requested DVM operation has completed. See B8.2.2 Sync type DVM transaction flow.

6. After receiving all the SnpResp responses, the Miscellaneous Node sends a Comp response to the requesting node.

#### B8.2.1.1 DVM early Comp for Non-sync DVMOps

The Miscellaneous Node in the interconnect is permitted to send Comp for a Non-sync DVMOp without waiting to complete the required snooping of Request Nodes. Such a Miscellaneous Node must take the responsibility of ordering this Non-sync DVMOp against any Sync DVMOp received later from the same source. If a Miscellaneous Node cannot provide such an ordering guarantee, snooping must be complete before sending a Comp response for a Non-sync DVMOp.

A Miscellaneous Node that is enabled to send early Comp for a Non-sync DVMOp is permitted to opportunistically combine Comp and DBIDResp responses into a single CompDBIDResp response.

> **_NOTE:_** Sending of a Comp response early for Non-sync DVMOp reduces round-trip latency for DVMOp completion. This enables a greater number of DVMOp transactions to be pipelined from a single source.
>
> Such an early completion also enables a Sync DVMOp, which is waiting for completions of all related DVMOp transactions sent earlier from the same Request Node.

The Miscellaneous Node must still wait for the Snoop response for a Sync DVMOp to be received before sending a Comp to the Requester for that Sync DVMOp.

### B8.2.2 Sync type DVM transaction flow

Figure B8.2 shows the flow in a Sync DVM transaction.