            - The Requester sends write data, CopyBackWriteData, to the Home.

                The Requester must only send this after receiving the CompDBIDResp response.

    2. **Not WriteEvictOrEvict and not CopyAtHome request**

        The request is not WriteEvictOrEvict and the CAH bit value in the request is set to 0.

        - The Home sends a combined data request and completion response, CompDBIDResp, to the Requester.
        - The Requester sends write data, CopyBackWriteData, to the Home. The Requester must only send this after receiving the CompDBIDResp response.

#### B2.3.2.4 Combined Immediate Write and CMO

Figure B2.6 shows the possible transaction flows for a Combined Write and CMO transaction. This only covers Non-persist Cache Maintenance Operations, see B2.3.2.5 Combined Immediate Write and Persist CMO for transaction flows for a Combined Immediate Write and Persist CMO transaction.