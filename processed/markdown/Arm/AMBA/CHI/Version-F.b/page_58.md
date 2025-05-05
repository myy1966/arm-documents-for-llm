        - Optionally, when the original request has an ordering requirement, the Home returns a read receipt, ReadReceipt, to the Requester.
        - The Home requests a Snoopee to forward read data, Snp\*Fwd, to the Requester. See B4.4 Request transactions and corresponding Snoop requests to determine which Snp*Fwd transactions can be used.
        - The alternatives, 5a-5d, show how the Snoopee can process the transaction:

            - **Alt 5a. With response to Home**

                - The Snoopee provides a combined response and read data, CompData, to the Requester.
                - The Snoopee provides a snoop response, SnpRespFwded, to the Home.

            - **Alt 5b. With data to Home**

                - The Snoopee provides a combined response and read data, CompData, to the Requester.
                - The Snoopee provides a Snoop response with data, SnpRespDataFwded, to the Home.

            - **Alt 5c. Failed, must use alternative**

                - The Snoopee provides a snoop response, SnpResp, to the Home.
                - The Home must use another alternative described in this section to complete the transaction to the Requester.

            - **Alt 5d. Failed, must use alternative**

                - The Snoopee provides a snoop response with data, SnpRespData or SnpRespDataPtl, to the Home.
                - The Home must use another alternative described in this section to complete the transaction to the Requester.

    - If the original request has ExpCompAck asserted, the Requester must only provide a CompAck response after the following:
    - At least one CompData packet is received.
    - RespSepData, if the request does not have an ordering requirement. The request is permitted, but not required, to wait for DataSepResp.
    - RespSepData and at least one DataSepResp packet, if the request has an ordering requirement.

If the original request has an ordering requirement, it is permitted, but not required, for the Requester to wait for ReadReceipt before sending CompAck.

Table B2.6 lists the permitted DMT and DCT transactions for ReadNoSnp and ReadOnce* from a Request Node. The following key is used:

- Y Yes, permitted

- N No, not permitted

- \- The flow is not used in the transaction

Table B2.6: Permitted DMT and DCT for ReadNoSnp and ReadOnce* from a Request Node

|   Order[1:0] |   ExpCompAck | DMT   | DCT   | Notes                                                                                                                                                                                                  |
|--------------|--------------|-------|-------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           00 |            0 | Y     | Y     | Home does not need to be notified of transaction completion. For DMT, Home must obtain a ReadReceipt from Subordinate Node to ensure the request to Subordinate Node is not given a RetryAck response. |

Continued on next page