    - The PGroupID is set to the same value as the PGroupID of the original request.

3. The recipient Home Node in the interconnect sends a Comp response to the Requester.

    The identifier fields of the Comp response to the Requester are generated as follows:

    - The TgtID is set to the same value as the SrcID of the original request.
    - The SrcID is a fixed value for the Home.
    - The TxnID is set to the same value as the TxnID of the original request.

4. The recipient Home Node can optionally send a Persist response to the Requester.

    The identifier fields of the optional Persist response from the Home Node to the Requester, not shown in Figure B2.27, are generated as follows:

    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Home Node.
    - The TxnID is inapplicable and must be set to 0.
    - The PGroupID is set to the same value as the PGroupID of the request.

    The recipient Home Node can optionally send a combined CompPersist response to the Requester, instead of separate Comp and Persist responses.

    The identifier fields in the CompPersist response are generated as follows:

    - The TgtID is set to the same value as the SrcID of the original request.
    - The SrcID is a fixed value for the Home.
    - The TxnID is set to the same value as the TxnID of the original request.
    - The PGroupID is set to the same value as the PGroupID of the original request.

5. The Subordinate Node generates a Comp to the Home Node.

    The identifier fields of the Comp response from the Subordinate Node are generated as follows:

    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Subordinate.
    - The TxnID is set to the same value as the TxnID of the request.

6. The Subordinate Node also generates a Persist response to either to the Requester or the Home.

    The identifier fields of the Persist response from the Subordinate Node are generated as follows:

    - The TgtID is set to the same value as the ReturnNID of the request.
    - The SrcID is a fixed value for the Subordinate.
    - The TxnID is inapplicable and must be set to 0.
    - The PGroupID is set to the same value as the PGroupID of the request.

7. The Subordinate Node can optionally send a combined CompPersist response to the Home Node, instead of separate Comp and Persist responses if the ReturnNID and SrcID of the request are the same value.

    The identifier fields of the CompPersist response from the Subordinate are generated as follows:

    - The TgtID is set to the same value as the SrcID of the request.
    - The SrcID is a fixed value for the Subordinate.
    - The TxnID is set to the same value as the TxnID of the request.
    - The PGroupID is set to the same value as the PGroupID of the request.