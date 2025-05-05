**Snoop response without data to Home and DCT**

- This Snoop response is used when the Snoopee sends Data to the Requester and a data transfer to the Home is not required.
- It is sent on the SRSP channel and uses the SnpRespFwded opcode.

**Snoop response with data**

- This Snoop response is used when a full cache line of data is transferred to Home.
- It is sent on the WDAT channel and uses the SnpRespData opcode.
- For Stash snoops, a DataPull request can be included.

**Snoop response with partial data**

- This Snoop response is used when a partial cache line of data is transferred to the Home.
- It is sent on the WDAT channel and uses the SnpRespDataPtl opcode.
- For Stash snoops, a DataPull request can be included.
- It is sent when the combination of the Snoop request and cache line state is:

    - Any Snoop request except SnpMakeInvalid, and the cache line state is UDP.

**Snoop response with data to Home and DCT**

- This Snoop response is used when the Snoopee sends Data to the Requester and a data transfer to the Home is also required.
- It is sent on the DAT channel and uses the SnpRespDataFwded opcode.

The Snoop response includes the Resp field, which indicates the following:

**Cache state** The final state of the cache line at the snooped node after sending the Snoop response.

**Pass Dirty** Indicates that the responsibility for updating memory is passed to the Requester or Interconnect. Pass Dirty must only be asserted for a Snoop response with data. The assertion of the Pass Dirty bit is shown by \_PD in the response name.

The Snoop response also includes the FwdState field that is applicable in Snoop responses with DCT and indicates the cache state and pass dirty value in the CompData response sent to the Requester.

The Snoop response attributes convey sufficient information for the interconnect to determine both:

- The appropriate response to the initial Requester
- If data must be written back to memory.

The Snoop response attributes are also sufficient to support snoop filter or directory maintenance in the interconnect.

See B12.9 Snoop requests for details on Snoop responses and MTE interaction.