The RespErr field in the response is used for this purpose. See B13.10.47 Response Error, RespErr. The RespErr field value of 0b01, Exclusive Okay, indicates a pass and a RespErr field value of 0b00, Normal Okay, indicates an Exclusive access failure.

The Exclusive Okay response must only be given for a transaction that has the Excl attribute set.

Not all memory locations are required to support Exclusive accesses. An Exclusive Load transaction to a location that does not support Exclusive accesses must not be given an Exclusive Okay response.

It is IMPLEMENTATION DEFINED whether or not Exclusive Store transaction to a location that does not support Exclusive accesses updates the location.

It is recommended that an Exclusive Store transaction is not performed to a location that does not support Exclusive accesses.

ReadPreferUnique and MakeReadUnique do not use RespErr to determine the pass or fail of an Exclusive operation. An Exclusive MakeReadUnique response with Shared cache state indicates the failure of an Exclusive access. When the response cache state is Unique, the Requester must use its Local Monitor state to determine if the Exclusive access is a pass.

Table B6.2 shows the Snoopable attributes of the request, the relevant monitor type and possible reasons for fail conditions and response requirements.

Table B6.2: Responses to an Exclusive access request

| Request type                                                          | Snoopable | Monitor type     | Fail condition                              | Response                                                                        |
|-----------------------------------------------------------------------|-----------|------------------|---------------------------------------------|---------------------------------------------------------------------------------|
| ReadNoSnp(Excl)                                                       | No        | System           | Target does not support Exclusive accesses  | Target must return a data response                                              |
| WriteNoSnp(Excl)                                                      | No        | System           | Address content modified                    | The Requester must still complete the write flow by sending the Data message    |
| WriteNoSnp(Excl)                                                      | No        | System           | Address not present due to monitor overflow |                                                                                 |
| WriteNoSnp(Excl)                                                      | No        | System           | Target does not support Exclusive accesses  |                                                                                 |
| ReadClean(Excl) </br> ReadNotSharedDirty(Excl) </br> ReadShared(Excl) | Yes       | LP, PoC          | Target does not support Exclusive accesses  | Target must return a data response                                              |
| ReadPreferUnique                                                      | Yes       | LP, optional PoC | None                                        | If a PoC monitor is available, the appropriate monitor bit                      |
| CleanUnique(Excl)                                                     | Yes       | LP, PoC          | Address content modified                    | Target must return a Comp response                                              |
| CleanUnique(Excl)                                                     | Yes       | LP, PoC          | Address not present due to monitor overflow |                                                                                 |
| CleanUnique(Excl)                                                     | Yes       | LP, PoC          | Target does not support Exclusive accesses  |                                                                                 |
| MakeReadUnique(Excl)                                                  | Yes       | LP, optional PoC | Address content modified                    | Target uses PoC monitor, Precise snoop filter, or SnpQery to determine response |
