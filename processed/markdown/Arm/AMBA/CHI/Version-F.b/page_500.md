Chapter B16. Properties, Parameters, and Broadcast Signals B16.1. Interface properties and parameters

- IO deallocation transactions
- ReadNotSharedDirty transaction
- CleanSharedPersist transaction
- Receiving of forwarding snoops.

Table B16.13 shows the Enhanced\_Features property options.

Table B16.13: Enhanced\_Features property options

| Enhanced\_Features value | Description                                                                                      |
|--------------------------|--------------------------------------------------------------------------------------------------|
| True                     | The component support the features that are covered by the Enhanced\_Features property.          |
| False or Not specified   | The component does not support the features that are covered by the Enhanced\_Features property. |

### B16.1.15 Deferrable\_Write

The Deferrable\_Write property is used to indicate whether a component supports WriteNoSnpDef transaction.

Table B16.14 shows the Deferrable\_Write property options.

Table B16.14: Deferrable\_Write property options

| Deferrable\_Write value | Description                    |
|-------------------------|--------------------------------|
| True                    | WriteNoSnpDef is supported     |
| False or Not specified  | WriteNoSnpDef is not supported |

### B16.1.16 RME\_Support

An RME\_Support property determines whether an interface supports RME transactions.

Table B16.15 shows the RME\_Support property options.

Table B16.15: RME\_Support property options

| RME\_Support value | Description                                                                                                                                                         |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| True               | The interface supports RME transactions. </br> RME\_Support can only be True if Nonshareable\_Cache\_Maint property is True and DVM\_Support property is DVM\_v9.2. |

### B16.1.17 Nonshareable\_Cache\_Maint

A Nonshareable\_Cache\_Maint property is used to indicate if an RN-F or interconnect supports the cache maintenance of a Non-snoopable cacheable location from a Requester that is different to the Requester that