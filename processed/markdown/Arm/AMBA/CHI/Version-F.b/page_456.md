### B13.10.35 SnoopMe

This field indicates that the Home must determine whether to send a snoop to the Requester. See B2.3.3 Atomic transactions.

Only applicable in Atomic requests.

Table B13.27 shows the SnoopMe value encodings.

Table B13.27: SnoopMe value encodings

| SnoopMe | Description                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| 0       | Home is permitted, but not required, to send a snoop to the Requester.                       |
| 1       | Home must send a Snoop to the Requester if the cache line could be present at the Requester. |

### B13.10.36 Return to Source, RetToSrc

This field requests the Snoopee to return a copy of the cache line to the Home.

RetToSrc is inapplicable and must be set to 0 in:

- SnpCleanShared, SnpCleanInvalid, and SnpMakeInvalid
- SnpOnceFwd and SnpUniqueFwd
- SnpUniqueStash, SnpMakeInvalidStash, SnpStashUnique, and SnpStashShared
- SnpQuery

RetToSrc is applicable and can take any value in all other snoops except SnpDVMOp.

RetToSrc is inapplicable and must be set to 0 in SnpDVMOp.

For RetToSrc bit semantics, see B4.9 Returning Data with Snoop response.

### B13.10.37 Data Pull, DataPull

This field indicates the inclusion of a Read request, also referred to as a Data Pull, in the Snoop response. See B7.1.1 Snoop requests and Data Pull.

Applicable in SnpResp, SnpRespData, and SnpRespDataPtl response to a Stash request, not applicable in all other Snoop responses.

When the DataPull bit is set in a SnpRespData message, it must be set in all packets of that response message.

Table B13.28 shows the DataPull field value encodings.

Table B13.28: DataPull value encodings

| DataPull      | Description | Comment                                      |
|---------------|-------------|----------------------------------------------|
| 0b000         | No read     | Inclusion of Data Pull in the Snoop response |
| 0b001         | Read        | Inclusion of Data Pull in the Snoop response |
| 0b010 - 0b111 | -           | Reserved                                     |