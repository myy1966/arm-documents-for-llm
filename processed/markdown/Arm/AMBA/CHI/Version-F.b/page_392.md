> - A Snoop response in response to a SnpDVMOp request.
> - Data response from the Subordinate Node in response to a Read request.
> - Spawned requests from HN-F:
>
>     - Snoops generated in response to a request from the Request Node.
>     - Request to SN-F generated in response to a request from the Request Node.
>
> - Spawned request from HN-I:
>
>     - Read or Write request to SN-I generated in response to a request from the Request Node.
>
> - A CompAck from the Request Node in response to CompData, Comp, or RespSepData.
> - A RetryAck response from the Home Node or the Subordinate Node to any request.
> - A ReadReceipt response from the Home Node or the Subordinate Node to a Read request or from the Subordinate Node to a ReadNoSnpSep request.
> - A DBIDResp response to a Write request.