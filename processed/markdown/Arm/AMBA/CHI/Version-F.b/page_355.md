    - ReadClean
    - ReadNotSharedDirty
    - ReadShared
    - ReadUnique
    - ReadPreferUnique
    - MakeReadUnique
    - CleanUnique
    - MakeUnique

- For a deallocating transaction:

    - The Requester must continue as normal, in a protocol-compliant manner.
    - The deallocating transactions are:

        - WriteBack
        - WriteEvictFull
        - Evict
        - WriteEvictOrEvict

- For Other transactions that do not change allocation:

    - The Requester must not upgrade the cache state.
    - The Requester is permitted to downgrade the cache state.

The cache state in a SnpResp message with a NDERR must be I. The Completer must invalidate local cached copies of the cache line. In addition, when the response to a Forwarding snoop results in a NDERR, the Snoopee must not forward data to the Requester. As a consequence, if the CompData message has already been sent to the Requester, the Snoop response to the Home must not include the NDERR.

### B9.1.4 Error response use by transaction type

This section defines the permitted, but not required, use of the error fields for each transaction type.

The tables that follow show the Data and Response packets associated with the following transaction types:

- B9.1.4.1 Read transactions
- B9.1.4.2 Dataless transactions
- B9.1.4.3 Write transactions
- B9.1.4.4 Atomic transactions
- B9.1.4.5 Other transactions
- B9.1.4.6 Cache Stashing transactions
- B9.1.4.7 Snoop transactions

The following keys are used by the tables:

- OK The RespErr field must contain the OK RespErr value of 0b00.
- Y This value of RespErr is permitted.
- N This value of RespErr is not permitted.
- \- Data or Response packet is not used for this transaction type.

#### B9.1.4.1 Read transactions

Read transactions can contain multiple CompData data packets.

Read data which is known to be corrupt must have an appropriate Error indication where the error can be Poison, DERR, or NDERR.

When RespSepData includes a NDERR, all corresponding DataSepResp packets must be marked with NDERR.