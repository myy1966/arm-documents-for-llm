### B13.10.56 Poison

This field indicates if the 64-bit chunk of data corresponding to a Posion bit is poisoned, that is, has an error, and must not be consumed. See B9.2.1 Poison.

Table B13.41 shows the Poison value encodings.

Table B13.41: Poison value encodings

| Poison | Description                                |
|--------|--------------------------------------------|
| 0      | Corresponding 64-bit chunk is not poisoned |
| 1      | Corresponding 64-bit chunk is poisoned     |

### B13.10.57 Data source, DataSource

This field identifies the Sender of the data response. See B11.2.1 DataSource value assignment.

Applicable in CompData and DataSepResp responses in Read and Atomic transactions, and SnpRespData and SnpRespDataPtl responses in Non-stash type Snoop transactions. DataSource is not applicable, and must be set to 0, in all other responses.

Table B13.42 shows the fixed values for DataSource when Data comes from memory. In Table B13.42, the following applies:

**R = 0** The memory is local

**R = 1** The memory is remote.

Table B13.42: Fixed values for DataSource

| DataSource        | Description                                                                 | Comments                                                                                                                                 |
|-------------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| 0bR0000           | DataSource is not supported, or Completer is not sending useful information | Applicable only if the Completer is a non-memory component                                                                               |
| 0bR0001 - 0bR0101 | IMPLEMENTATION DEFINED                                                      | See B11.2.2.1 Suggested DataSource values                                                                                                |
| 0bR0110           | PrefetchTgt memory prefetch was useful                                      | Read data was obtained from Completer with lower latency as the PrefetchTgt request already read or initiated a read of data from memory |

Continued on next page