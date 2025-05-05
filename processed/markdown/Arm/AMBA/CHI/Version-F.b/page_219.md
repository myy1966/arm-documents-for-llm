## B4.5 Response types

Each request can generate one or more responses. Some responses can also include data. A Response is classified as follows:

- B4.5.1 Completion response
- B4.5.2 WriteData response
- B4.5.3 Snoop response
- B4.5.4 Miscellaneous response

### B4.5.1 Completion response

A completion response is required for all transactions except PCrdReturn and PrefetchTgt. It is typically the last message sent from the Completer, to conclude a request transaction. However, the Requester could still send a CompAck response to conclude the transaction. A completion guarantees that the request has reached a PoS or a PoC, where it will be ordered with respect to requests to the same address from any Requester in the system. See B2.6 Ordering for details on the Ordering guarantees.

#### B4.5.1.1 Read and Atomic transaction completion

A Read completion is either in the form of a single response on the RDAT channel using the CompData opcode, or two separate responses, one on the RSP channel using the RespSepData opcode and a second one on the RDAT channel using the DataSepResp opcode. See B4.5.1.2 Dataless transaction completion for completion without data for the MakeReadUnique transaction.

AtomicLoad, AtomicSwap, and AtomicCompare completion is sent on the RDAT channel and uses the CompData opcode.

The CompData and DataSepResp completion responses include the Resp field that indicates the following:

**Cache state** The final permitted state of the cache line at the Requester for all reads except ReadNoSnp and ReadOnce.

**Pass Dirty** Indicates if the responsibility for updating memory is passed to the Requester. The assertion of the Pass Dirty bit is shown by \_PD in the response name.

When using separate Comp and Data responses, RespSepData also includes the Resp field with Cache state and Pass Dirty indications. The Resp field value in RespSepData must be either inapplicable and set to 0 or the same as in the corresponding DataSepResp.

Table B4.26 shows the permitted Read transaction completion, the encoding of the Resp field, and the meaning of the response. A Subordinate Node can send DataSepResp only in response to ReadNoSnpSep, and only CompData in response to ReadNoSnp.

Table B4.26: Permitted Read transaction completion and Resp field encodings

| Response       | Resp[2:0] | Final cache line state | Notes                                                            |
|----------------|-----------|------------------------|------------------------------------------------------------------|
| CompData\_I    | 0b000     | I                      | Indicates that a coherent copy of the cache line cannot be kept. |
| RespSepData\_I | 0b000     | Not applicable         | Cache state must be determined from DataSepResp response.        |

Continued on next page