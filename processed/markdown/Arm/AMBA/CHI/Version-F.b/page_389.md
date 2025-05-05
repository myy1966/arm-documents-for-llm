## B11.6 Completer Busy

The Completer Busy indication is a mechanism for the Completer of a transaction to indicate its current level of activity. Completer Busy provides additional information to a Requester on how aggressive speculative activity can be generated to improve performance.

**CBusy** Completer Busy. A 3-bit field that is applicable in the appropriate DAT and RSP packets. When separate Data and Comp responses are used for a single Read request, the Busy indication in each response can be independently set.

The CBusy field is not applicable in:

- NonCopyBackWriteData
- NonCopyBackWriteDataCompAck
- CopyBackWriteData
- WriteDataCancel
- CompAck

> **_NOTE:_** DataSource can be used as a qualifier to the Completer Busy indication such that some data sources, for example a Forwarding snoop, do not influence the busy indication.

### B11.6.1 Use case

It is IMPLEMENTATION DEFINED how a CBusy indication is set by the Completer and how CBusy should be interpreted by a Requester. However, it is recommended that implementations consider mechanisms to avoid a few busy Completers among many skewing the results.

#### B11.6.1.1 Example use case

The following is an example encoding of the CBusy field.

CBusy[2] When asserted, this indicates multiple cores are actively making requests.

CBusy[1:0] Indicates the degree of fullness of the tracker at the Completer as:

- 00 = Less than 50% full
- 01 = Greater than 50% full
- 10 = Greater than 75% full
- 11 = Greater than 90% full

The prefetcher at the Requester can use the CBusy field values and fine-tune the prefetcher.

Table B11.6 shows the prefetcher mode that is determined by the value of CBusy.