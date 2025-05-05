                    - Sends CompAck to the Home. The Requester must only send this after it has received DBIDResp, DBIDRespOrd, CompDBIDResp, or Comp. It is permitted, but not required, to wait for DBIDResp or DBIDRespOrd before sending CompAck. It is not permitted to wait for Comp or CompCMO before sending CompAck.

                - **Alt 3b2b. Combined response from Requester**

                    The Requester sends a combined write data and completion acknowledge, NonCopyBackWriteDataCompAck, to the Home. The Requester must only send this after it has received DBIDResp, DBIDRespOrd, or CompDBIDResp. It is not permitted to wait for Comp before sending NonCopyBackWriteDataCompAck if DBIDResp or DBIDRespOrd have been received. It is not permitted to wait for CompCMO before sending NonCopyBackWriteDataCompAck.

    - The Home returns a CMO completion response, CompCMO, to the Requester. It is permitted, but not required, for the Home to wait for write data from the Requester before returning CompCMO.

#### B2.3.2.5 Combined Immediate Write and Persist CMO

Figure B2.7 shows the possible transaction flows for Combined Immediate Write and Persist CMO transaction.