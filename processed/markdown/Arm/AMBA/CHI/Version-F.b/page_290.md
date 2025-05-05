The steps in Figure B5.18 are:

1. RN-F0 sends an Atomic transaction to HN-F.
2. After receiving the Atomic request, HN-F:

    - Sends DBIDResp to RN-F0 to obtain the Atomic transaction data.
    - Sends SnpUnique Snoop request to other RN-Fs after determining that snoops are required.
    - HN-F is permitted, but not required, to send a speculative ReadNoSnp to SN-F.

3. RN-F2 has the cache line in UD state and responds by sending data and invalidating its own cached copy.

    - The response is SnpRespData\_I\_PD.
    - This data is marked as (InitialData) in Figure B5.18 to be distinguishable from the data sent by the Requester and the data written to SN-F after the atomic operation is executed.
    - HN-F also receives a second Snoop response, SnpResp\_I, from RN-F1.

4. After receiving all Snoop responses, HN-F sends CompData\_I to the Requester.

    - The data sent with Comp is the initial copy of the data.
    - This data must not be cached in a coherent state at RN-F0.

5. In response to the DBIDResp sent previously, HN-F receives the NonCopyBackWriteData\_I response from the Requester.

    - This data is marked as (TxnData) in Figure B5.18 to be distinguishable from the data sent by RN-F2 in response to the Snoop request from HN-F.

6. Once HN-F receives the NonCopyBackWriteData\_I response from the Requester, and the Snoop response with data from RN-F2, the atomic operation is executed.

    - The resulting value after atomic operation execution, marked as (NewData) in Figure B5.18, is written to SN-F.

7. In this example, the read data received due to the speculative read is discarded by HN-F.

> **_NOTE:_** In Figure B5.18, the CompData\_I response from HN-F can be sent when all Snoop responses are received.
>
> Alternatively, to aid error reporting, CompData\_I can be delayed until NonCopyBackWriteData is received from the Requester and the atomic operation is executed.

#### B5.4.1.2 Atomic transaction without snoops and with data return

Figure B5.19 shows the atomic operation executed at the Home Node.