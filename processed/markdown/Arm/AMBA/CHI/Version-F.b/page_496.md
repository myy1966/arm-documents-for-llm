Table B16.2: Cache\_Stash\_Transaction property options

| Cache\_Stash\_Transactions value | Description                                    |
|----------------------------------|------------------------------------------------|
| True                             | Cache Stashing transactions are supported.     |
| False or Not specified           | Cache Stashing transactions are not supported. |

### B16.1.3 Direct\_Memory\_Transfer

A Direct\_Memory\_Transfer property is used to indicate if a component supports Direct Memory Transfer transactions.

Table B16.3 shows the Direct\_Memory\_Transfer property options.

Table B16.3: Direct\_Memory\_Transfer property options

| Direct\_Memory\_Transfer value | Description                                            |
|--------------------------------|--------------------------------------------------------|
| True                           | Direct Memory Transfer transactions are supported.     |
| False or Not specified         | Direct Memory Transfer transactions are not supported. |

The Direct\_Memory\_Transfer property is defined at each Home Node for each Subordinate Node.

### B16.1.4 Data\_Poison

A Data\_Poison property is used to indicate if a component supports Poison.

Table B16.4 shows the Data\_Poison property options.

Table B16.4: Data\_Poison property options

| Data\_Poison value     | Description                                                                   |
|------------------------|-------------------------------------------------------------------------------|
| True                   | Poison is supported and the Poison field is present in the DAT packet         |
| False or Not specified | Poison is not supported and the Poison field is not present in the DAT packet |

### B16.1.5 Direct\_Cache\_Transfer

A Direct\_Cache\_Transfer property is used to indicate if a component supports Direct Cache Transfer transactions.

Table B16.5 shows the Direct\_Cache\_Transfer property options.