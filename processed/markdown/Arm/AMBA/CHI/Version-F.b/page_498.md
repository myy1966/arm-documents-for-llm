### B16.1.8 CleanSharedPersistSep\_Request

A CleanSharedPersistSep\_Request property is used to indicate if a component supports CleanSharedPersistSep. Table B16.7 shows the CleanSharedPersistSep\_Request property options.

Table B16.8: CleanSharedPersistSep\_Request property options

| CleanSharedPersistSep\_Request value | Description                                                                                                              |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| True                                 | The component supports CleanSharedPersistSep                                                                             |
| False or Not specified               | The component does not support CleanSharedPersistSep and the component must not be sent a CleanSharedPersistSep request. |

The CleanSharedPersistSep\_Request property has the following conditions:

- A Home that receives a CleanSharedPersistSep request must support such a request.
- A Home can track if a connected Subordinate supports CleanSharedPersistSep.
- If a Subordinate does not support CleanSharedPersistSep:

    - The Home must send a CleanSharedPersist instead of a CleanSharedPersistSep request to that Subordinate.
    - Home must take the responsibility of sending the Persist response to the Requester. This Persist response must only be sent after receiving the Comp response from the Subordinate.

- A Requester that does not support CleanSharedPersistSep generates CleanSharedPersist instead.

### B16.1.9 MPAM\_Support

The MPAM\_Support property is used to indicate whether an interface supports MPAM.

Table B16.9 shows the MPAM\_Support property options.

Table B16.9: MPAM\_Support property options

| MPAM\_Support value    | Description                                                                                                                                                                                                                                        |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MPAM\_9\_1             | The interface is enabled for partitioning and monitoring: </br> - The MPAM field must be included on the REQ, DAT, and SNP channels. </br> - The width of PartID is 9 bits, the width of PerfMonGroup is 1 bit, and the width of MPAMSP is 2 bits. |
| False or Not specified | MPAM is not supported: </br> - The interface is not MPAM enabled. </br> - No MPAM fields are present on the interface.                                                                                                                             |

How the MPAM field values are used by a Receiver is IMPLEMENTATION DEFINED.