## B4.10 Do not transition to SD

Do not transition to SD (DoNotGoToSD) is a field that modifies Non-invalidating snoops.

DoNotGoToSD specifies when a Snoopee must not transition to SD state as a result of the Snoop request.

> **_NOTE:_** A non-forced change or silent change from UD to SD is permitted irrespective of the value of DoNotGoToSD.
>
> Any forced change from Unique to Shared must obey DoNotGoToSD.

See B13.10.38 Do not transition to SD state, DoNotGoToSD for the field applicability and field value encoding.