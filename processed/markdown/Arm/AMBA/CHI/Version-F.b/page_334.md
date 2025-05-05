Table B8.3 Continued from previous page

| Field name  | Restriction                                 |
|-------------|---------------------------------------------|
| Addr        | (Req\_Addr\_Width) - 3. See DVM Operations. |
| NS          | Must be 0.                                  |
| NSE         | Must be 0.                                  |
| DoNotGoToSD | Must be 0.                                  |
| RetToSrc    | Must be 0.                                  |
| TraceTag    | None.                                       |
| MPAM        | Must be all zeros.                          |

Both SnpDVMOp request packets, corresponding to a single DVMOp, must have the same value in the following fields:

- TxnID
- Opcode
- SrcID

### B8.3.4 Data DVMOp field value restrictions

Table B8.4 shows the Data message field value restrictions for a DVMOp transaction.

Table B8.4: Data message field value restrictions for DVMOp

| Field name          | Restriction                                                  |
|---------------------|--------------------------------------------------------------|
| QoS                 | None. Can take any value.                                    |
| TgtID               | Must be the same as SrcID returned in the DBIDResp response. |
| SrcID               | Must be ID of the original Requester.                        |
| TxnID               | Must be the same as DBID of the DBIDResp response.           |
| HomeNID PBHA        | Must be all zeros.                                           |
| Opcode              | Must be NonCopyBackWriteData.                                |
| RespErr             | Must be 0b00 or 0b10.                                        |
| Resp                | Must be all zeros.                                           |
| FwdState DataSource | Must be all zeros.                                           |
| DataPull            | Must be 0.                                                   |
| CBusy               | Must be all zeros.                                           |

Continued on next page