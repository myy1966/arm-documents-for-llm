See B4.7.1.1 MakeReadUnique transaction and B6.3.1.1 MakeReadUnique(Excl) to see how SnpQuery can be used in the efficient handling of exclusive request flows.

**SnpDVMOp**

Generated at the interconnect, initiated by the DVMOp request:

- A single DVMOp request generates two snoop requests.
- Returns a single Snoop response for the two Snoop requests.

See B8.2.1 Non-sync type DVM transaction flow.