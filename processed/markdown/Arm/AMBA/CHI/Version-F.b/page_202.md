> addition to a completion response, a separate Persist response is required for the CMO part of the request.

Table B4.18 and Table B4.19 show the permitted combinations of Write and CMO requests. Table B4.18 and Table B4.19 use the following key:

- Y Yes, permitted
- \- Not permitted

Table B4.18: Permitted combinations of Write and CMO for Request Node to Home Node requests

| Write type                                     | PCMO </br> With separate Persist response | Non-persistent CMO </br> CleanShared | Non-persistent CMO </br> CleanInvalid or CleanInvalidPoPA | Non-persistent CMO </br> MakeInvalid |
|------------------------------------------------|-------------------------------------------|--------------------------------------|-----------------------------------------------------------|--------------------------------------|
| WriteNoSnpFull </br> WriteNoSnpPtl             | Y                                         | Y                                    | Y                                                         | -                                    |
| WriteNoSnpDef                                  | -                                         | -                                    | -                                                         | -                                    |
| WriteUniqueFull </br> WriteUniquePtl           | Y                                         | Y                                    | -                                                         | -                                    |
| WriteUniqueStashFull </br> WriteUniqueStashPtl | -                                         | -                                    | -                                                         | -                                    |
| WriteBackFull                                  | Y                                         | Y                                    | Y                                                         | -                                    |
| WriteBackPtl                                   | -                                         | -                                    | -                                                         | -                                    |
| WriteCleanFull                                 | Y                                         | Y                                    | -                                                         | -                                    |
| WriteEvictFull                                 | -                                         | -                                    | -                                                         | -                                    |

Table B4.19: Permitted combinations of Write and CMO for Home Node to Subordinate Node requests

| Write type                         | PCMO </br> With separate Persist response | Non-persistent CMO </br> CleanShared | Non-persistent CMO </br> CleanInvalid or CleanInvalidPoPA | Non-persistent CMO </br> MakeInvalid |
|------------------------------------|-------------------------------------------|--------------------------------------|-----------------------------------------------------------|--------------------------------------|
| WriteNoSnpFull </br> WriteNoSnpPtl | Y                                         | Y                                    | Y                                                         | -                                    |
| WriteNoSnpDef                      | -                                         | -                                    | -                                                         | -                                    |

Examples of how combining of a Write request with Cache Maintenance is useful are:

- Combining WriteBack with CleanShared and CleanSharedPersist, supports Request Nodes that transition the cache line to Invalid when cleaned by a CMO irrespective of the type of CMO.
- Combining WriteUnique with CleanShared supports the case when the CleanSharedPersist target is known to not support Persistent transactions. Therefore, the CleanSharedPersist request needs to be converted to CleanShared by the Requester.

For each Write request the Combined Write requests are: