for CompCMO and CompPersist. See B7.3 Independent Stash request for CompStashDone.

#### B4.5.1.3 Write and Atomic transaction completion

A Write and AtomicStore completion is sent on the CRSP channel and uses the Comp or CompDBIDResp opcode.

No cache state information, or responsibility for a Dirty cache line, is communicated using the Write transaction completion. The Resp field of a Comp or CompDBIDResp response must be set to zero for any Write transaction completion, except for a WriteNoSnpDef transaction. See B4.5.1.3.1 WriteNoSnpDef for more information. All cache state information and responsibility for a Dirty cache line are communicated with the WriteData. See B4.5.2 WriteData response.

The permitted Write transaction completion responses are:

**Comp** Used when the completion response is separate from the DBIDResp or DBIDRespOrd response.

**CompDBIDResp** Used when the completion response is combined with the DBIDResp or DBIDRespOrd response.

All CopyBack requests must use the CompDBIDResp completion response. Immediate writes and AtomicStore, can either send Comp and DBIDResp or DBIDRespOrd responses separately or can opportunistically combine the two responses and send CompDBIDResp if both are ready to be sent to the Requester.

##### B4.5.1.3.1 WriteNoSnpDef

The permitted Resp field and RespErr field value combinations in Comp or CompDBIDResp responses for WriteNoSnpDef transactions are shown in Table B4.28.