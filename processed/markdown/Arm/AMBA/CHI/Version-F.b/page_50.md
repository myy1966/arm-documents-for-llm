Table B2.5 Continued from previous page

| Field     | Description                                                                                                                      |
|-----------|----------------------------------------------------------------------------------------------------------------------------------|
| DataID    | Data Identifier. Provides the address offset of the data provided in the packet. See B2.8 Data transfer.                         |
| TagOp     | Tag Operation. As defined in Table B2.2. See B13.10.40 Tag Operation, TagOp.                                                     |
| Tag       | Memory Tag. Provides sets of 4-bit tags. Each tag is associated with an aligned 16-byte of data. See B13.10.41 Tag.              |
| TU        | Tag Update. Indicates which of the Allocation Tags must be updated. See B13.10.42 Tag Update, TU.                                |
| TraceTag  | Trace Tag. As defined in Table B2.2. See Chapter B11 System Control,Debug, Trace, and Monitoring.                                |
| CAH       | Debug, Trace, and Monitoring CopyAtHome. In responses from Home or a Snoopee, indicates if the Home keeps a copy of the line that is provided to the Requester. Also defined in Table B2.2. For more information, see B13.10.30 CopyAtHome, CAH. |
| RSVDC     | User-defined. See B13.10.59 Reserved for Customer Use, RSVDC.                                                                    |
| BE        | Byte Enable. For a data write, or data provided in response to a snoop, indicates which bytes are valid. See B2.8 Data transfer. |
| Data      | Data payload. See B2.8 Data transfer.                                                                                            |
| DataCheck | Data Check. Detects Data Errors in the DAT packet. See B9.2.2 Data Check.                                                        |
| Poison    | Poison. Indicates that a set of data bytes has previously been corrupted. See B9.2.1 Poison.                                     |