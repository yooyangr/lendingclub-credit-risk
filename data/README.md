# Data setup

The source dataset is intentionally excluded from this repository because the cleaned Feather file is approximately 545 MB and the underlying LendingClub data remains subject to its original distribution terms.

To reproduce the analysis:

1. Obtain the historical LendingClub loan dataset from an authorized source.
2. Clean it so it includes the fields referenced in the notebook, including `loan_status`, loan terms, borrower financial indicators, credit-history fields, and loan grades.
3. Save the cleaned table as:

   ```text
   data/lending_club_clean.feather
   ```

Alternatively, point the notebook to an existing cleaned file:

```powershell
$env:LENDINGCLUB_DATA = 'C:\path\to\lending_club_clean.feather'
```

No raw borrower records are committed to this repository.
