Table B4.37 Continued from previous page

| Request type     | Initial expected state | Initial permitted state | Final state | Comp responses   | Separate responses                |
|------------------|------------------------|-------------------------|-------------|------------------|-----------------------------------|
| ReadShared       | I, UCE ᵃ               | -                       | SC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadShared       | I, UCE ᵃ               | -                       | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadShared       | I, UCE ᵃ               | -                       | SD          | CompData\_SD\_PD | -                                 |
| ReadShared       | I, UCE ᵃ               | -                       | UD          | CompData\_UD\_PD | RespSepData + DataSepResp\_UD\_PD |
| ReadUnique       | I, SC                  | UC, UCE                 | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadUnique       | I, SC                  | UC, UCE                 | UD          | CompData\_UD\_PD | RespSepData + DataSepResp\_UD\_PD |
| ReadUnique       | SD ᵉ                   | UD, UDP ᵉ               | UD          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadUnique       | SD ᵉ                   | UD, UDP ᵉ               | UD          | CompData\_UD\_PD | RespSepData + DataSepResp\_UD\_PD |
| ReadPreferUnique | I, SC                  | UCE                     | SC          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadPreferUnique | I, SC                  | UCE                     | UC          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadPreferUnique | I, SC                  | UCE                     | UD          | CompData\_UD\_PD | RespSepData + DataSepResp\_UD\_PD |
| ReadPreferUnique | SD ᵈ ᵉ                 | -                       | SD          | CompData\_SC     | RespSepData + DataSepResp\_SC     |
| ReadPreferUnique | SD ᵈ ᵉ                 | -                       | UD          | CompData\_UC     | RespSepData + DataSepResp\_UC     |
| ReadPreferUnique | SD ᵈ ᵉ                 | -                       | UD          | CompData\_UD\_PD | RespSepData + DataSepResp\_UD\_PD |

- ᵃ For ReadNotSharedDirty and ReadShared transactions, the Requester with an initial state of UCE must not upgrade the cache line to UDP or UD while the request is outstanding.
- ᵇ A Requester in initial state of UC that receives a CompData_SC or DataSepResp_SC response must stay in UC state. Similarly, a Home that uses a Snoop filter to track the cached state at the Requester, must not downgrade the state of the cache line in the snoop filter based on the state in the response to the Requester.
- ᶜ A Requester in initial state of UD that receives a CompData\_SC or DataSepResp\_SC response must stay in UD state. Similarly, a Home that uses a Snoop filter to track the cached state at the Requester, must not downgrade the state of the cache line in the snoop filter based on the state in the response to the Requester.
- ᵈ A Requester in initial state of SD that receives a CompData\_SC or DataSepResp\_SC response must stay in SD state. Similarly, a Home that uses a Snoop filter to track the cached state at the Requester, must not downgrade the state of the cache line in the snoop filter based on the state in the response to the Requester.
- ᵉ Data received from memory must be dropped if the cache state is UD or SD, or merged if the cache state is UDP. Data received from memory must be the same as the cached data when the cache state is SC or UC.