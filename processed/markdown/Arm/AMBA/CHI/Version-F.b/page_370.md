Table B9.18 Continued from previous page

| Channel   | Check signal   | Signals covered   | Check signal width   | Check granularity   | Check enable   |
|-----------|----------------|-------------------|----------------------|---------------------|----------------|
| SNP       | SNPFLITPENDCHK | SNPFLITPEND       | 1                    | 1                   | RESETn == 1    |
| SNP       | SNPFLITVCHK    | SNPFLITV          | 1                    | 1                   | RESETn == 1    |
| SNP       | SNPFLITCHK     | SNPFLIT           | ceil(S/8) ᶜ          | 1 to 8              | SNPFLITV == 1  |
| SNP       | SNPLCRDVCHK    | SNPLCRDV          | 1                    | 1                   | RESETn == 1    |
| DAT       | DATFLITPENDCHK | DATFLITPEND       | 1                    | 1                   | RESETn == 1    |
| DAT       | DATFLITVCHK    | DATFLITV          | 1                    | 1                   | RESETn == 1    |
| DAT       | DATFLITCHK     | DATFLIT           | ceil(D/8) ᶜ          | 1 to 8              | DATFLITV == 1  |
| DAT       | DATLCRDVCHK    | DATLCRDV          | 1                    | 1                   | RESETn == 1    |

- ᵃ R = Request flit width. See B13.9.1 Request flit.
- ᵇ T = Response flit width. See B13.9.2 Response flit.
- ᶜ S = Snoop flit width. See B13.9.3 Snoop flit.
- ᵈ D = Data flit width. See B13.9.4 Data flit.