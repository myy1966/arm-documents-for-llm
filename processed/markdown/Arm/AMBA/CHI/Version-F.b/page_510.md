Table C1.1 shows the conventions used in the field mapping tables.

Table C1.1: Key to field mapping table conventions

| Symbol   | Description                                                                                                                                                                                                   |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CF       | Common Field. Two or more protocol message fields share the same set of bits in this packet field.                                                                                                            |
| X        | Inapplicable. Field value can take any value.                                                                                                                                                                 |
| 1        | Applicable. Field value is used, must be set to 1.                                                                                                                                                            |
| 0        | Applicable. Field value is used, must be set to 0.                                                                                                                                                            |
| 0ᵃ       | Inapplicable. Field value must be set to 0.                                                                                                                                                                   |
| Y        | Applicable. Field value is used. See specification for permitted values and usage.                                                                                                                            |
| D        | Inapplicable. Field value must be default setting for MPAM fields.                                                                                                                                            |
| 8B       | Size field must be set to 8-byte encoding.                                                                                                                                                                    |
| 64B      | Size field must be set to 64-byte encoding.                                                                                                                                                                   |
| M        | Field position reused for DVM operations. See (DVM Operations)                                                                                                                                                |
| -        | Assigned to another protocol message field that shares the same set of bits in this packet field. If the other field is not present, then it is considered inapplicable and the field value must be set to 0. |