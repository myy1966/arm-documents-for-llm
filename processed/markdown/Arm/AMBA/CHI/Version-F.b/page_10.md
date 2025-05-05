| subchapter                     | subsubchapter                       | page number |
|--------------------------------|-------------------------------------|-------------|
| B7.1 Overview                  |                                     | 317         |
|                                | B7.1.1 Snoop requests and Data Pull | 317         |
| B7.2 Write with Stash hint     |                                     | 319         |
| B7.3 Independent Stash request |                                     | 320         |
| B7.4 Stash target identifiers  |                                     | 322         |
|                                | B7.4.1 Stash target specified       | 322         |
|                                | B7.4.2 Stash target not specified   | 322         |
| B7.5 Stash messages            |                                     | 323         |
|                                | B7.5.1 Supporting REQ packet fields | 323         |
|                                | B7.5.2 Supporting SNP packet fields | 324         |
|                                | B7.5.3 Supporting RSP packet field  | 324         |
|                                | B7.5.4 Supporting DAT packet field  | 324         |

### Chapter B8 DVM Operations

| subchapter                            | subsubchapter                                  | page number |
|---------------------------------------|------------------------------------------------|-------------|
| B8.1 Introduction to DVM transactions |                                                | 326         |
| B8.2 DVM transaction flow             |                                                | 327         |
|                                       | B8.2.1 Non-sync type DVM transaction flow      | 327         |
|                                       | B8.2.2 Sync type DVM transaction flow          | 328         |
|                                       | B8.2.3 Flow control                            | 330         |
| B8.3 DVMOp field value restrictions   |                                                | 331         |
|                                       | B8.3.1 Request DVMOp field value restrictions  | 331         |
|                                       | B8.3.2 Response DVMOp field value restrictions | 332         |
|                                       | B8.3.3 Snoop DVMOp field value restrictions    | 333         |
|                                       | B8.3.4 Data DVMOp field value restrictions     | 334         |
| B8.4 DVM messages                     |                                                | 336         |
|                                       | B8.4.1 DVM message payload                     | 336         |
|                                       | B8.4.2 DVM message packing                     | 342         |
|                                       | B8.4.3 TLB Invalidate                          | 344         |
|                                       | B8.4.4 Branch Predictor Invalidate             | 348         |
|                                       | B8.4.5 Instruction Cache Invalidate            | 348         |
|                                       | B8.4.6 Synchronization                         | 350         |

### Chapter B9 Error Handling

| subchapter                                  | subsubchapter                                   | page number |
|---------------------------------------------|-------------------------------------------------|-------------|
| B9.1 Packet level                           |                                                 | 353         |
|                                             | B9.1.1 Error types                              | 353         |
|                                             | B9.1.2 Error response fields                    | 353         |
|                                             | B9.1.3 Errors and transaction structure         | 354         |
|                                             | B9.1.4 Error response use by transaction type   | 355         |
| B9.2 Sub-packet level                       |                                                 | 366         |
|                                             | B9.2.1 Poison                                   | 366         |
|                                             | B9.2.2 Data Check                               | 366         |
|                                             | B9.2.3 Interoperability of Poison and DataCheck | 367         |
| B9.3 Use of interface parity                |                                                 | 368         |
|                                             | B9.3.1 Byte parity check signals                | 368         |
|                                             | B9.3.2 Error detection behavior                 | 369         |
|                                             | B9.3.3 Interface parity check signals           | 369         |
| B9.4 Hardware and software error categories |                                                 | 371         |
|                                             | B9.4.1 Software-based error                     | 371         |
|                                             | B9.4.2 Hardware-based error                     | 371         |

### Chapter B10 Realm Management Extension

| subchapter                        | subsubchapter                        | page number |
|-----------------------------------|--------------------------------------|-------------|
| B10.1 Introduction                |                                      | 373         |
| B10.2 Physical Address Space, PAS |                                      | 374         |
| B10.3 Cache maintenance           |                                      | 375         |
|                                   | B10.3.1 Cache Maintenance Operations | 375         |