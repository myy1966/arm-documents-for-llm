Table B9.16: Legal RespErr field values in Response packets for Forwarding Snoop transactions

| Snoop transaction            | Associated Response packets </br> SnpResp </br> OK | Associated Response packets </br> SnpResp </br> EXOK | Associated Response packets </br> SnpResp </br> DERR | Associated Response packets </br> SnpResp </br> NDERR | Associated Response packets </br> SnpRespFwded </br> OK | Associated Response packets </br> SnpRespFwded </br> EXOK | Associated Response packets </br> SnpRespFwded </br> DERR | Associated Response packets </br> SnpRespFwded </br> NDERR |
|------------------------------|----------------------------------------------------|------------------------------------------------------|------------------------------------------------------|-------------------------------------------------------|---------------------------------------------------------|-----------------------------------------------------------|-----------------------------------------------------------|------------------------------------------------------------|
| SnpOnceFwd </br> SnpCleanFwd | Y                                                  | N                                                    | N                                                    | Y                                                     | Y                                                       | N                                                         | Y                                                         | N                                                          |

Table B9.17 shows the Forwarding Snoop Data response packets legal RespErr field values.

Table B9.17: Legal RespErr field values in Data packets for Forwarding Snoop transactions

| Snoop transaction    | Associated Data packets   | Associated Data packets   | Associated Data packets   | Associated Data packets   |          |          |          |       |
|----------------------|---------------------------|---------------------------|---------------------------|---------------------------|----------|----------|----------|-------|
|                      | SnpRespData               | SnpRespData               | SnpRespData               | SnpRespData               | CompData | CompData | CompData |       |
|                      | SnpRespDataFwded          | SnpRespDataFwded          | SnpRespDataFwded          | SnpRespDataFwded          |          |          |          |       |
|                      | OK                        | EXOK                      | DERR                      | NDERR                     | OK       | EXOK     | DERR     | NDERR |
| SnpOnceFwd           | Y                         | N                         | Y                         | N                         | Y        | N        | Y        | N     |
| SnpCleanFwd          |                           |                           |                           |                           |          |          |          |       |
| SnpNotSharedDirtyFwd |                           |                           |                           |                           |          |          |          |       |
| SnpSharedFwd         |                           |                           |                           |                           |          |          |          |       |
| SnpUniqueFwd         |                           |                           |                           |                           |          |          |          |       |
| SnpPreferUniqueFwd   |                           |                           |                           |                           |          |          |          |       |