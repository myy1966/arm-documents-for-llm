### B16.1.10 CCF\_Wrap\_Order

See B2.8.7 Critical Chunk First Wrap order.

### B16.1.11 Req\_Addr\_Width

The Req\_Addr\_Width parameter is used to indicate the maximum PA supported by a component.

Table B16.10 shows the Req\_Addr\_Width parameter options.

Table B16.10: Req\_Addr\_Width parameter options

| Req\_Addr\_Width value | Description        |
|------------------------|--------------------|
| 44 to 52               | Legal values       |
| Not specified          | Defaul value is 44 |

### B16.1.12 NodeID\_Width

The NodeID\_Width parameter is used to indicate the width of NodeID fields supported by a component, which determines the maximum NodeID value in the system.

Table B16.11 shows the NodeID\_Width parameter options. The width specified in Table B16.11 is uiformly applied to all NodeID related fields.

Table B16.11: NodeID\_Width parameter options

| NodeID\_Width value | Description       |
|---------------------|-------------------|
| 7 to 11             | Legal values      |
| Not specified       | Defaul value is 7 |

### B16.1.13 Data\_Width

The Data\_Width parameter is used to indicate the data width in the DAT channel packet supported by a component.

Table B16.12 shows the Data\_Width parameter options.

Table B16.12: Data\_Width parameter options

| Data\_Width value | Description         |
|-------------------|---------------------|
| 128, 256, and 512 | Legal values        |
| Not specified     | Defaul value is 128 |

### B16.1.14 Enhanced\_Features

The Enhanced\_Features property describes the combined support for the following features:

- Data return from SC state