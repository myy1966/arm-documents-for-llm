The steps in the WriteBackFull transaction flow in Figure B5.17 are:

1. RN-F0 sends WriteBackFull request to HN-F.
2. HN-F returns CompDBIDResp to RN-F0. RN-F0 cache line state transitions from UD to I.
3. RN-F0 sends CBWrData\_UD\_PD to HN-F. HN-F sends WriteNoSnp to SN-F.
4. SN-F returns CompDBIDResp to HN-F.
5. HN-F sends NCBWrData to SN-F.