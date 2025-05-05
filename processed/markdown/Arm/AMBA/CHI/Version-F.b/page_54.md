The sequence for the Allocating Read transaction is:

- The transaction starts with the Requester issuing an Allocating Read request to the Home. The initial request is one of the following:

    - ReadClean
    - ReadNotSharedDirty
    - ReadShared
    - ReadUnique
    - ReadPreferUnique
    - MakeReadUnique

- Alternatives 1-6 show different ways that the Home can process the transaction:

    1. **Combined response from Home**

        The Home returns a combined response and read data, CompData, to the Requester. Typically, this option is used by the Home when data and response can be returned at the same time. An example is when the data is cached locally.

    2. **Separate data and response from Home**

        The Home returns a separate response, RespSepData, and read data, DataSepResp, to the Requester. Typically, this option is used by the Home when a response can be returned quicker than the Home can provide the data.

    3. **Combined response from Subordinate**

        - The Home sends a downstream read request, ReadNoSnp, to the Subordinate.
        - Optionally, when the Home requests a ReadReceipt response, the Subordinate returns a read receipt, ReadReceipt, to the Home.
        - The Subordinate returns a combined response and read data, CompData, to the Requester.

        Typically, this option is used by the Home either to reduce the message count or reduce design complexity.

    4. **Response from Home, Data from Subordinate**

        - The Home returns a separate response, RespSepData, to the Requester.
        - The Home sends a downstream read data only request, ReadNoSnpSep, to the Subordinate.
        - The Subordinate returns a read receipt, ReadReceipt, to the Home. It is permitted, but not required, for the Home to wait for ReadReceipt from the Subordinate before sending RespSepData to the Requester.
        - The Subordinate returns read data, DataSepResp, to the Requester. Typically, this option is used by the Home when a response can be returned quickly. However, the Home does not have the data available and requires the Subordinate to return the data.

            > **_NOTE:_** In many circumstances, the Requester receives RespSepData far in advance to DataSepResp. The Requester is permitted, but not required, to send the CompAck response after receiving RespSepData without waiting for DataSepResp. The prompt response from the Requester, and potentially receiving ReadReceipt around the same time, permits the Home to complete the transaction faster than when using combined completion and data responses from the Subordinate.

    5. **Forwarding snoop**