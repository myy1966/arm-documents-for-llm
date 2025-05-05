## B11.2 Data Source indication

It is permitted, but not required, for the Completer of a Read request to specify the source of the data. The source is specified in the DataSource field of the CompData, DataSepResp, SnpRespData, and SnpRespDataPtl responses. DataSource field value is valid even in data responses with error.

The DataSource field can also be used to transport information to bias SLC replacement policy. See B11.3 SLC Replacement Hint.

### B11.2.1 DataSource value assignment

The DataSource value assignment uses the following key:

- **R = 0** The memory is local.
- **R = 1** The memory is remote.

The DataSource values must be assigned as follows:

- Fixed values are used for DataSource when data comes from memory and are used to indicate the following:

    - **0bR0110** PrefetchTgt memory prefetch was useful. Read data was obtained from the Subordinate with lower latency as the PrefetchTgt request already read or initiated a read of data from memory.
    - **0bR0111** PrefetchTgt memory prefetch was not useful. Read request went through a complete memory access and therefore did not have any latency reduction due to the PrefetchTgt request sent earlier. The precise reason for signaling that a prefetch was not useful is IMPLEMENTATION DEFINED.

        > **_NOTE:_** There are several reasons why the PrefetchTgt request could not be useful. Examples are that the prefetch was dropped by the Subordinate, the data obtained by the prefetch was replaced in the buffer, or the Read request arrived at the Subordinate before the prefetch.

- When a system has only a local chip and no concept of remote, the DataSource[4] bit can be reused for additional local chip granularity for DataSource.
- For a response from a cache, not memory, the DataSource value is IMPLEMENTATION DEFINED. It is recommended, but not required, to use certain values for DataSource in these cases. A component is permitted, but not required, to have software programmability to override the DataSource value to:

    - Change the groupings to more suitable specific configuration settings.
    - Change the values where the values are not correct.

- A Completer is permitted to not support sending a useful DataSource value, in which case:

    - The Completer, except for a memory SN-F, must return a 0bR0000 value.
    - A memory SN-F component must return 0bR0111 as a default value. Such exceptions must be understood by the system.

### B11.2.2 Crossing a chip-to-chip interface

The chip interface module, if one exists, is responsible to map DataSource values in the incoming data packets to different values to identify that the response came from the remote chip.