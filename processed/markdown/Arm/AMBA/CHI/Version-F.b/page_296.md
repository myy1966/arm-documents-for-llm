The steps in the AtomicStore transaction executed at SN-F in Figure B5.22 are:

1. RN-F0 sends an AtomicStore transaction to HN-F.

    - The Atomic request is to a Snoopable address location.

2. After receiving the Atomic request, HN-F:

    - Sends DBIDResp to RN-F0 to obtain the Atomic transaction data.
    - Sends a SnpUnique to other RN-Fs after determining that snoops are required.

3. RN-F2 has the cache line in UD state and responds by sending data and invalidating its own cached copy.

    - The response is SnpRespData\_I\_PD.
    - This data is marked as (InitialData) in Figure B5.22 to be distinguishable from the data sent by the Requester and the data written to SN-F to execute the atomic operation.
    - HN-F also receives a second Snoop response, SnpResp\_I, from the other snooped RN-F.

4. HN-F writes the received data to SN-F using a WriteNoSnp transaction.
5. In response to the DBIDResp sent previously, HN-F receives the NonCopyBackWriteData response from the Requester.
6. HN-F after sending the Snoop response data to SN-F, sends an AtomicStore transaction request to SN-F, and executes the sequence of messages required to complete the Atomic transaction.
7. The HN-F deallocates the request once the Comp response is sent to the Requester and the Comp response for the Atomic transaction is received from SN-F.

    - The Comp response from HN-F can be sent when all the Snoop responses are received.