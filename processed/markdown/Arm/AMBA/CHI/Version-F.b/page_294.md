> **_NOTE:_** In Figure B5.21, the read from the Subordinate Node is required to obtain the InitialData and is not speculative.
>
> The Comp response from the Home Node can be combined with the DBIDResp response.

The steps in the AtomicStore transaction executed at the Home Node in Figure B5.21 are:

1. RN sends AtomicStore request to the HN.
2. HN returns DBIDResp response to RN, indicating the RN can send the write data to the HN.
3. HN sends Comp response to RN and sends ReadNoSnp request to the SN.
4. SN returns RespData\_I to the HN.
5. Once the HN has the write data from the RN, the atomic operation is executed and WriteNoSnp is sent to SN.
6. SN returns CompDBIDResp to the HN.
7. HN sends the result of the atomic operation to the SN, marked as NewData.

### B5.4.3 Atomic operation executed at the SN

Figure B5.22 shows an example Atomic transaction flow where the SN-F is executing the atomic operation.