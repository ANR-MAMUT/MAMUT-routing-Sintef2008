# Changelog: Sintef2008 benchmark family

All notable changes to the Sintef2008 family are recorded here. The first entry records the creation of this repository. The section after it holds the changelog that the family had in the main MAMUT-routing repository. It keeps every entry, fact, date, count and commit reference, with the wording edited for style and the headings moved 2 levels down.

## 2026-11: family repository

- The family, tracked until now directly in the main MAMUT-routing repository, becomes the repository `MAMUT-routing-Sintef2008`, mounted in MAMUT-routing at `benchmarks/Sintef2008`. Its history is extracted from the history of the main repository, under the directory of its problem type. `history/` holds the map from the former to the new commit identifiers.
- Instances and best-known solutions keep their former path after the problem type, for example `VRPTW/n=1000/C1_10_10.vrp.json`.
- No data changes. No instance, no best-known solution and no instance identifier changed. Only the location changed.
- `mamut-collection.json` at the root marks the repository as a family collection (`"layout_version": 2`).
- This layout is read by `mamut-routing-lib` 0.13 and later, which is in development and not released yet. `mamut-routing-lib` 0.12 and earlier read the former layout, which stays available read-only in the archive of the former main repository, `MAMUT-routing-archive-2026-11`.
- The README, LICENSE and CHANGELOG files move from `VRPTW/` to the root, and CITATION.cff and NOTICE files are added. LICENSE now contains the MIT License text that it refers to.

## Former VRPTW directory of the main repository

### Changelog of the Sintef2008 BKS

All notable changes to the curated `Sintef2008` best-known solutions (BKS) are recorded here. Objective: **hierarchical** (minimize number of vehicles first, then total travel distance). Costs are Euclidean double-precision distances. Routes are stored in a deterministic order (sorted by first customer ID) so that floating-point aggregation is reproducible and any strict improvement is real.

#### 2026-06-15

Re-scraped the [SINTEF TOP VRPTW website](https://www.sintef.no/projectweb/top/vrptw/) and adopted newly-available official SINTEF solutions wherever they **strictly improve** the curated hierarchical BKS. 7 Solomon `n=100` instances that were previously absent from SINTEF are now published there. 5 of them beat the heuristic placeholders we had been carrying (the other 2 matched the existing BKS and were left unchanged). All replacements keep the same vehicle count and reduce the total travel distance.

| Instance | n | Vehicles | Cost (before → after) | Δ cost | Previous source |
|---|---:|---:|---|---:|---|
| R203  | 100 | 3  | 967.7541501389894 → 939.5033196327311  | −28.25  | ils_best |
| R207  | 100 | 2  | 997.4948714387555 → 890.6082953143248  | −106.89 | nbrmh |
| RC107 | 100 | 11 | 1263.1597438752965 → 1230.4774501448208 | −32.68  | pyvroom_hier |
| RC202 | 100 | 3  | 1816.1482334842403 → 1365.6450311683866 | −450.50 | nbrmh |
| RC203 | 100 | 3  | 1074.6158005793240 → 1049.6242367397950 | −24.99  | ils_best |

All 5 new solutions were validated with `mamut-routing-lib` (`check_solution`) and adopted only when strictly better under the hierarchical objective (`is_better_solution`). Their cost matches SINTEF's reported value to ~1e-12 (stored under `metadata.sintef_reported_cost`).

##### Metadata

- Removed the non-portable `source_path` field from every `Sintef2008` BKS. It referenced a path inside the (not-yet-public) scraping repository and carried no value for downstream users. Provenance is still captured by `source`, `authors`, `date`, and (where applicable) `reference` / `sintef_reported_cost`.
