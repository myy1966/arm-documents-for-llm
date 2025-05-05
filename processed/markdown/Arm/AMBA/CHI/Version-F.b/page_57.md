The sequence for the Non-allocating Read transactions is:

- The transaction starts with the Requester issuing a Read request to the Home. The Non-allocating Read transactions are:

    - ReadNoSnp
    - ReadOnce
    - ReadOnceCleanInvalid
    - ReadOnceMakeInvalid

    The request contains the following fields which affect the transaction flow:

    - Order
    - ExpCompAck

- Alternatives 1-6 show how the Home can process the transaction. For a description of the typical use of the different alternatives, see B2.3.1.1 Allocating Read.

    1. **Combined response from Home**

        - Optionally, when the original request has an ordering requirement, the Home returns a read receipt, ReadReceipt, to the Requester.
        - The Home returns a combined response and read data, CompData, to the Requester.

    2. **Separate data and response from Home**

        The Home returns a separate response, RespSepData, and read data, DataSepResp, to the Requester. This alternative cannot be used if the request has an ordering requirement and a completion acknowledge is not required.

    3. **Combined response from Subordinate**

        - Optionally, when the original request has an ordering requirement, the Home returns a read receipt, ReadReceipt, to the Requester.
        - The Home sends a downstream read request, ReadNoSnp, to the Subordinate.
        - Optionally, when the Home requests a ReadReceipt response, the Subordinate returns ReadReceipt to the Home. The Home must do this when a completion acknowledge is not required. It is permitted, but not required, for the Home to wait for ReadReceipt from the Subordinate before returning ReadReceipt to the Requester.
        - The Subordinate returns a combined response and read data, CompData, to the Requester.

        This alternative cannot be used if the request has an ordering requirement and a completion acknowledge is not required.

    4. **Response from Home, data from Subordinate**

        - The Home returns a separate response, RespSepData, to the Requester and sends a downstream read data only request, ReadNoSnpSep, to the Subordinate.
        - Optionally, when the Home requests a ReadReceipt response, the Subordinate returns a read receipt, ReadReceipt, to the Home. The Home must request a ReadReceipt unless the original request indicates a requirement for both ordering and a completion acknowledge. It is permitted, but not required, for the Home to wait for ReadReceipt from the Subordinate before returning RespSepData to the Requester.
        - The Subordinate returns read data, DataSepResp, to the Requester.

        This alternative cannot be used if the request has an ordering requirement and a completion acknowledge is not required.

    5. **Forwarding snoop**