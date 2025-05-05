    > **_NOTE:_** However, there is a loss of the ability to reduce the write data bandwidth for CopyBack Write transactions if the cached CAH attribute is cleared unnecessarily.

    - A Requester is not required to clear the CAH attribute to 0 when a WriteClean request is sent.

- When a Requester has a cache line with a CAH value of 0, a CopyBack transaction must not be sent with the CAH attribute in the request set to 1.
- When a Requester has a cache line with a CAH value of 1, it is expected, but not required, to send a CopyBack transaction with the CAH attribute as 1.

    - Once a CopyBack request has been sent with the CAH attribute set to 1, the Requester must not further modify the cache line until the transaction completes.
    - Once a WriteCleanFull request has been sent from a UD state with the CAH attribute set to 1, the Requester must ensure that any later updates to the line are not lost if the Home completes the transaction without requesting a data transfer.

- When supplying CompData in response to a forwarding snoop, a Snoopee is expected, but not required, to forward the CAH value to the Requester. If the Snoopee does not forward the CAH value, the value must be set to 0 in the CompData response.
- When supplying SnpRespData or SnpRespDataFwded to Home in response to a snoop, a Snoopee is expected, but not required, to send the CAH value. If the Snoopee does not send the CAH value, it then must be set to 0 in the data response.

For CopyBack Write transactions, the Resp field value in a CompAck response is applicable and must indicate the state of the cache at the point the CompAck response is sent. If a snoop request is received while the CopyBack Write is outstanding, the cache line state can differ from the cache line state when the original transaction was sent. See B4.7.3 Write request transactions for more information.

The cache line state information in the CompAck response must be used by the Home to determine whether any hidden copy of the line the Home has can be exposed. See Table B2.15 Home can take for each CompAck response.

Table B2.15: Permitted CompAck responses for CopyBack Write transactions

| Response        | Resp[2:0] | Cache line state when the response was sent | Action when a hidden copy of the cache line exists at Home                           | Notes                                                    |
|-----------------|-----------|---------------------------------------------|--------------------------------------------------------------------------------------|----------------------------------------------------------|
| CompAck\_I      | 0b000     | Imprecise and must be ignored               | Must not yet be exposed                                                              | Indicates a CopyBack request has been canceled           |
| CompAck\_UC     | 0b010     | UC                                          | Expose, unless a Unique copy exists elsewhere ᵃ. This is expected, but not required. |                                                          |
| CompAck\_SC     | 0b001     | SC                                          | Expose. This is expected, but not required.                                          |                                                          |
| CompAck\_UD\_PD | 0b110     | UD                                          | Expose, unless a Unique copy exists elsewhere ᵃ. This is expected, but not required. | Responsibility for updating memory is passed to the Home |

Continued on next page