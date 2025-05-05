##### B2.7.4.1.3 Device RE

The required behavior for the Device RE memory type is same as for the Device nRE memory type, except:

- Read and Write transactions from the same source to the same endpoint need not remain ordered.
- Read and Write transactions from the same source to addresses that overlap must remain ordered.

##### B2.7.4.1.4 Normal Non-cacheable Non-bufferable

The required behavior for the Normal Non-cacheable Non-bufferable memory type is:

- The write response must be obtained from the final destination.
- Read data must be obtained from the final destination.
- Writes can be merged.
- Read and Write transactions from the same source to addresses that overlap must remain ordered.

##### B2.7.4.1.5 Normal Non-cacheable Bufferable

The required behavior for the Normal Non-cacheable Bufferable memory type is:

- The write response can be obtained from an intermediate point.
- Write transactions must be made visible at the final destination in a timely manner.

> **_NOTE:_** There is no mechanism to determine when a Write transaction is visible at its final destination.

- Read data must be obtained either from:

    - The final destination.
    - A Write transaction that is progressing to its final destination.

        If read data is obtained from a Write transaction:

        - The data must be obtained from the most recent version of the write.
        - The data must not be cached to service a later read.

- Writes can be merged.
- Read and Write transactions from the same source to addresses that overlap must remain ordered.

> **_NOTE:_** For a Normal Non-cacheable Bufferable read, data can be obtained from a Write transaction that is still progressing to its final destination. This is indistinguishable from the Read and Write transactions propagating to arrive at the final destination at the same time. Read data returned in this manner does not indicate that the Write transaction is visible at the final destination.

##### B2.7.4.1.6 Write-Back No-allocate

The required behavior for the Write-Back No-allocate memory type is:

- The Write response can be obtained from an intermediate point.
- Write transactions are not required to be made visible at the final destination.
- Read data can be obtained from an intermediate cached copy.
- Reads can be prefetched.
- Writes can be merged.
- A cache lookup is required for Read and Write transactions.