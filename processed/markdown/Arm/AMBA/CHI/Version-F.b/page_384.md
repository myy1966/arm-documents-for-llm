The SLCRepHint field is only applicable in requests from a Request Node to HN-F.

The field is inapplicable in requests from the Request Node to HN-I and the Home Node to the Subordinate Node. The field can take any value.

The field is inapplicable in requests from the Request Node to the Subordinate Node, and must be set to 0.

Table B11.3 shows the suggested Replacement subfield encodings and their meaning.

Table B11.3: Suggested Replacement subfield encodings

| Replacement[2:0] | Description                      |
|------------------|----------------------------------|
| 0b000            | No recommendation (default)      |
| 0b100            | Most likely to be used again     |
| 0b101            | More likely to be used again     |
| 0b110            | Somewhat likely to be used again |
| 0b111            | Least likely to be used again    |
| 0b011-0b001      | Unused                           |