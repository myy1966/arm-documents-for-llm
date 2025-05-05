## B6.1 Overview

The principles of Exclusive accesses are that a Logical Processor (LP) performing an exclusive sequence does the following:

- Performs an Exclusive Load from a location.
- Calculates a value to store to that location.
- Performs an Exclusive Store to the location.

Exclusive accesses are supported to Snoopable and Non-snoopable memory locations.

If the location is updated by a different LP since the Exclusive Load, the Exclusive Store must fail. In this case, the store does not occur and the LP does not update the value held at the location.

Table B6.1 shows the descriptions for Exclusive terms.

Table B6.1: Description of Exclusive terms

| Term                        | Description of Exclusive terms                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exclusive Load              | The action of an LP executing an appropriate program instruction, such as LDREX, requires: - Obtaining the data from the location to which the LP wants to perform an exclusive sequence. - Indicating that the LP is starting an exclusive sequence.                                                                                                                                                                                                                                                                                |
| Exclusive Load transaction  | A transaction issued on the interface to obtain data for an Exclusive Load, if the data is not available in the cache at the LP. Not every Exclusive Load requires an Exclusive Load transaction.                                                                                                                                                                                                                                                                                                                                    |
| Exclusive Store             | The action of an LP executing an appropriate program instruction, such as STREX, requires: - Determining if the exclusive sequence has passed or failed. - If appropriate, updating the data at the location. Can pass or fail and this result is known to the executing processor. When an Exclusive Store passes, the data value at the address location is updated. When an Exclusive Store fails, this indicates that the data value at the address location has not been updated, and the exclusive sequence must be restarted. |
| Exclusive Store transaction | A transaction issued on the interface that could be required to complete an Exclusive Store. Not every Exclusive Store requires an Exclusive Store transaction. An Exclusive Store transaction can pass or fail and this result is made known to the LP using the transaction response.                                                                                                                                                                                                                                              |
