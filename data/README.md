# The data

Made from the SA Housing Trust's Private Rent Report and ABS data (both CC BY 4.0), see [`../NOTICE`](../NOTICE); our tables and shapes are CC BY 4.0.

- `tables/quarters.csv`: one row per Greater Adelaide suburb and quarter, March 2013 to June 2026 (53 quarters; the December 2014 report covers six months and is left out). `code` (ABS suburb code), `name`, `quarter` (2026-06 is April to June 2026), `rent` (the median weekly rent of new bonds, all dwellings, blank where it is not shown), `shown` (why not), `few` (fewer than 10 new bonds), `batch` (a one-off batch, left out), `bonds`, `median_all`, `houses_bonds`, `median_houses`, `units_bonds`, `median_units` (as printed; counts of 1 to 5 printed as `*` count as 3).
- `tables/suburbs.csv`: one row per Greater Adelaide suburb (ABS Suburbs and Localities, 2021): its SA2, bonds and typical rent in 2015 (the four quarters of 2015) and in the year to June 2026, for all dwellings, houses and units; `ok_*` is 1 where both years have 40 or more bonds, and only then is `change_pct_*` filled. `state`: compared, few bonds or no bonds. 2021 Census `persons` and `dwellings`.
- `tables/metro.csv`: Greater Adelaide by quarter: the suburbs' medians averaged, weighted by their bonds, for all dwellings, houses and units.
- `tables/rent_long.csv`: every suburb row of every report read, all of South Australia, with the report's own spelling and its Metro or Country flag.
- `tables/suburb_names.csv`: each spelling in the reports and the ABS suburb code Plotlay's matcher gave it (blank: no match, with suggestions).
- `tables/batches.csv`: the suburb quarters left out as one-off batches.
- `geometry/suburbs.*`: Greater Adelaide's suburbs as Plotlay made them from the ABS boundaries, keyed by ABS code (`key`).
