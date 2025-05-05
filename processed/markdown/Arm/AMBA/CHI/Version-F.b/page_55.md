        - The Home requests a Snoopee to forward read data, Snp\*Fwd, to the Requester. See B4.4 Request transactions and corresponding Snoop requests to determine which Snp*Fwd transactions can be used. Typically, this option is used by the Home when the data is not cached locally and the Home determines that a Snoopee is likely to have a copy.
        - Alternatives 5a-5d show how the Snoopee can process the transaction:

            - **Alt 5a. With response to Home**

                - The Snoopee returns a combined response and read data, CompData, to the Requester.
                - The Snoopee provides a snoop response, SnpRespFwded, to the Home. Typically, this option is used by the Snoopee when data can be forwarded to the Requester and is not required to provide a copy of data to the Home.

            - **Alt 5b. With data to Home**

                - The Snoopee returns a combined response and read data, CompData, to the Requester.
                - The Snoopee provides a snoop response with data, SnpRespDataFwded, to the Home.

                > **_NOTE:_** Typically, this option is used by the Snoopee when data can be forwarded to the Requester while also providing a copy of data to the Home. For example, when the Snoopee holds a Dirty copy of the cache line, but the data returned to the Requester must be Clean. This option can also happen when the Home has requested a copy of the data.

            - **Alt 5c. Failed via RSP channel, must use alternative**

                The Snoopee provides a snoop response, SnpResp, to the Home. The Home must use another alternative described in this section to complete the transaction to the Requester.

            - **Alt 5d. Failed via DAT channel, must use alternative**

                The Snoopee provides a snoop response with data, SnpRespData or SnpRespDataPtl, to the Home. The Home must use another alternative described in this section to complete the transaction to the Requester.

    6. **MakeReadUnique only**

        The Home returns a completion response, Comp, to the Requester. This option is only applicable for a MakeReadUnique transaction when a read data message is not required.

- The transaction ends when the Requester sends a completion acknowledge, CompAck, to the Home. The CompAck must only be sent after a CompData or RespSepData is received. It is permitted, but not required, to wait for DataSepResp before sending CompAck.

#### B2.3.1.2 Non-allocating Read

Figure B2.2 shows the possible transaction flows for a Non-allocating Read transaction.