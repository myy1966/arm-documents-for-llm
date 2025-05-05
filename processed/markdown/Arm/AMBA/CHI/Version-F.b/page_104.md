Use of this 8-bit field is applicable in Write requests where TagOp is set to Match, and in a TagMatch response. TagGroupID is inapplicable and must be set to 0 in all other requests and responses.

- TagGroupID must be sent in a Write request where TagOp is set to Match.
- The precise contents of TagGroupID are IMPLEMENTATION DEFINED. Typically, TagGroupID is expected to contain an Exception Level, TTBR value, and PE identifier.

See B13.10.43 Tag Group Identifier, TagGroupID.