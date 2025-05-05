Table B4.37 Continued from previous page

| Request type                  | Initial expected state            | Initial permitted state | Final state | Comp responses   | Separate responses                |
|-------------------------------|-----------------------------------|-------------------------|-------------|------------------|-----------------------------------|
| ReadClean TagOp = *Transfer*  | I                                 | -                       | SC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadClean TagOp = *Transfer*  | I                                 | -                       | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadClean TagOp = *Transfer*  | UC, UCE <sup>b</sup> <sup>e</sup> | -                       | UC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadClean TagOp = *Transfer*  | UC, UCE <sup>b</sup> <sup>e</sup> | -                       | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadClean TagOp = *Transfer*  | UD, UDP <sup>c</sup> <sup>e</sup> | -                       | UD          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadClean TagOp = *Transfer*  | UD, UDP <sup>c</sup> <sup>e</sup> | -                       | UD          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadClean TagOp = *Transfer*  | SC                                | -                       | SC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadClean TagOp = *Transfer*  | SC                                | -                       | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadClean TagOp = *Transfer*  | SD <sup>d</sup> <sup>e</sup>      | -                       | SD          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadClean TagOp = *Transfer*  | SD <sup>d</sup> <sup>e</sup>      | -                       | UD          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadClean TagOp != *Transfer* | I                                 | -                       | SC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadClean TagOp != *Transfer* | I                                 | -                       | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadClean TagOp != *Transfer* | UCE                               | -                       | UC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadClean TagOp != *Transfer* | UCE                               | -                       | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadNotSharedDirty            | I, UCE <sup>a</sup>               | -                       | SC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadNotSharedDirty            | I, UCE <sup>a</sup>               | -                       | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadNotSharedDirty            | I, UCE <sup>a</sup>               | -                       | UD          | CompData\_UD\_PD | RespSepData + DataSepResp\_UD\_PD |

Continued on next page