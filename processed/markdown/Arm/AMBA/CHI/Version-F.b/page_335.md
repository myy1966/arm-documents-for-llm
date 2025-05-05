Table B8.4 Continued from previous page

| Field name | Restriction                                                                |
|------------|----------------------------------------------------------------------------|
| DBID       | None. Can take any value.                                                  |
| CCID       | Must be all zeros.                                                         |
| DataID     | Must be all zeros.                                                         |
| TagOp      | Must be all zeros.                                                         |
| Tag        | Must be 0.                                                                 |
| TU         | Must be 0.                                                                 |
| TraceTag   | None.                                                                      |
| CAH        | Must be 0.                                                                 |
| RSVDC      | None.                                                                      |
| BE         | Only BE[7:0] must be asserted.                                             |
| Data       | Unused bits must be 0 for Data[63:0] and Data [n:64] = Can take any value. |
| DataCheck  | Must be the appropriate value for the Data field.                          |
| Poison     | None. Can take any value.                                                  |
