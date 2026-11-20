# Sintef2008 benchmark family (VRPTW)

Benchmark family repository of [MAMUT-routing](https://github.com/ANR-MAMUT/MAMUT-routing), mounted there as `benchmarks/Sintef2008`. It contains the MAMUT-routing curation of the classical Solomon/Gehring-Homberger VRPTW instances under the SINTEF 2008 hierarchical objective convention.

## Layout

- `VRPTW/n=<customers>/` holds the instances (`<Name>.vrp.json`) and their best-known solutions (`<Name>.bks.HierarchicalVehicleCost.json`), for example `VRPTW/n=1000/C1_10_10.vrp.json` and `VRPTW/n=1000/C1_10_10.bks.HierarchicalVehicleCost.json`.
- `mamut-collection.json` at the root marks the repository as a family collection (`"layout_version": 2`).
- `history/` holds the commit map of the former location of this family (see the history section below).

## Library compatibility

This layout is read by `mamut-routing-lib` 0.13 and later, which is in development and not released yet. `mamut-routing-lib` 0.12 and earlier read the former layout, which stays available read-only in the archive of the former main repository, [MAMUT-routing-archive-2026-11](https://github.com/ANR-MAMUT/MAMUT-routing-archive-2026-11).

## License scope

- MAMUT-routing-authored curation artifacts, normalized metadata, and contributed files are distributed under MIT where MAMUT-routing holds the relevant rights.
- The underlying benchmark definitions and some BKS sources originate from third-party historical benchmark material. This repository-level notice does not relicense those third-party sources.

Preserve this README, the LICENSE file of this repository, and the [NOTICE](NOTICE) file of this repository when redistributing this benchmark family.

## Citation

The citation metadata of this repository, with its authors and their ORCID identifiers, is recorded in [CITATION.cff](CITATION.cff). This family is a curation of third-party benchmarks, so also cite the original benchmark: Solomon (1987) and Gehring and Homberger (1999) for the instances, and the SINTEF VRPTW benchmark for the hierarchical objective convention. Record the exact Git commit used in experiments.

## History of this repository

Until November 2026 the family was tracked directly in the main MAMUT-routing repository, at `benchmarks/VRPTW/Sintef2008`. Its history was extracted from the history of the main repository and rewritten under the directory of its problem type (`VRPTW/`). Only the commits that touched this directory are kept, each with a new identifier. `history/commit-map-MAMUT-routing.tsv` maps the former commit identifiers of the main repository to the new ones, for the kept commits only. It is tab-separated, with the former commit identifier and the new one on each line, after a header line. See [CHANGELOG.md](CHANGELOG.md) for the reorganisation.
