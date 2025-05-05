    > **_NOTE:_** HN-F does not send snoops as the request is recognized as a Non-snoopable request type.

3. HN-F sends a ReadNoSnp to SN-F.
4. SN-F returns CompData\_I to HN-F.
5. HN-F in turn returns the data to RN-F0.

    > **_NOTE:_** If ExpCompAck had not been asserted in the original ReadNoSnp request, the HN-F could have deallocated the request at this point.

6. RN-F0 deallocates the request and sends CompAck towards the HN-F.
7. HN-F receives the CompAck response and deallocates the request.

The copy of data being transferred is marked in bold in Figure B5.5.

### B5.1.5 Read transaction with snoop response with partial data and no memory update

An example of this type of flow is a ReadUnique transaction.

Figure B5.6 shows the transaction flow, the copy of data being transferred is marked in bold.