Table B13.31 shows the TagOp value encodings.

Table B13.31: TagOp value encodings

| TagOp[1:0] | Tag Operation | Description                                                                                                                                                                                                                                                                  |
|------------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0b00       | Invalid       | The tags are not valid                                                                                                                                                                                                                                                       |
| 0b01       | Transfer      | - The tags are Clean. </br> - Tag Match does not need to be performed. </br> - All tags corresponding to data in the packet must be transferred. For Snoopable transactions, partial tag transfer is not supported. </br> - TU field is not applicable and must be set to 0. |
| 0b10       | Update        | - The Allocation Tag values have been updated and are Dirty. </br> - The Tags in memory should be updated. Only the Tags that have TU asserted must be updated.                                                                                                              |
| 0b11       | Match         | – The Physical Tags in the write must be checked against the Allocation Tag values obtained from memory. </br> – The Match Tag operation must be enabled for only those tags that have BE asserted. </br> – TU field is not applicable and must be set to 0                  |
| 0b11       | Fetch         | - Tags must be fetched. </br> - All tags must be fetched. </br> - Permitted, but not required, to fetch valid data.                                                                                                                                                          |

TagOp value in a Retry request must be the same as in the original request.

### B13.10.41 Tag

Tag[4*n-1:0]. This field provides n sets of 4-bit tags, each associated with a 16-byte, aligned address location.

[Tag[((4*n)-1) : 4*(n-1)] corresponds to Data[((128*n)-1 : 128*(n-1)]