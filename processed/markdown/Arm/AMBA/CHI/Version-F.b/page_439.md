Table B13.9 – Continued from previous page

<!-- MERGE table -->

DATFLIT[(D-1):0] format

| Field  | Field width                   | Comments        |
|--------|-------------------------------|-----------------|
| Poison | 0 or DW/64 = 2, 4, 8          | P = Poison      |
| Total  | D = (223 to 235) + Y + DC + P | DW=128-bit Data |
|        | D = (372 to 384) + Y + DC + P | DW=256-bit Data |
|        | D = (670 to 682) + Y + DC + P | DW=512-bit Data |