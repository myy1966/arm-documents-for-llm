4. RN-F2 returns SnpResp\_I to the HN-F. HN-F can now send Comp\_UC to RN-F0. RN-F0 cache line state transitions from SC to UC. Meanwhile, SN-F returns CompDBIDResp to HN-F. HN-F subsequently sends NCBWrData to SN-F.
5. RN-F0 issues CompAck response to the HN-F to indicate transaction completion.

### B5.2.3 Persistent CMO with snoop and separate Comp and Persist

In this example of CleanSharedPersistSep transaction flow, the Point of Persistence (PoP) is at the SN-F.

Figure B5.13 shows the transaction flow.

Figure B5.13: CleanSharedPersistSep transaction flow

![Image](page_282/image_000000_dfbf29742ffdf2d44fb7e27c617725a0cbbe8ce5092f36b6e096d1cd63e5c4ed.png)

The steps in the CleanSharedPersistSep transaction flow in Figure B5.13 are: