# Data provenance

Dates and source revisions below distinguish what can be verified from this
checkout from the versions originally used to create its CSV files. The
supplied checkout has no Git commits or acquisition records, so the original
download dates and exact source revisions for the CSVs are not recorded.
Repository revisions identified as "inspected" are provenance references,
not claims that the CSVs were obtained from those revisions.

## NextiaJD-S and NextiaJD-M

- Source: https://github.com/dtak-upc/NextiaJD/tree/master/experiments
- Source version used: Not recorded in the supplied checkout.
- Source revision inspected for provenance: `14e8a8611455785c4abeb87d5d9b7d1a2f480346` (commit dated 2022-06-15, touching `experiments`; inspected 2026-10-27).
- Date obtained: Not recorded in the supplied checkout.
- Source license: Apache License 2.0.
- DesJoin files:
  - `Benchmarks/Original/NextiaJD-S.csv`
  - `Benchmarks/Original/NextiaJD-M.csv`
  - `Benchmarks/Revised/NextiaJD-S.csv`
  - `Benchmarks/Revised/NextiaJD-M.csv`
- Transformation: Original and revised benchmark CSVs are both retained. The
  revised files contain manual review, corrections, and joinability
  annotations; they are modified derivative works.
- DesJoin contribution: Manual review, corrections, and joinability
  annotations in the revised files.

## Spider

- Source: https://yale-lily.github.io/spider
- Additional sources:
  - https://github.com/taoyds/spider
  - https://huggingface.co/datasets/xlangai/spider
- Source version used: Not recorded in the supplied checkout.
- Date obtained: Not recorded in the supplied checkout.
- Dataset license: Creative Commons Attribution-ShareAlike 4.0 International
  (CC BY-SA 4.0), as identified by the XLANG dataset source.
- DesJoin file: `Benchmarks/Original/Spider.csv`.
- Transformation: Converted to the CSV format used in the DesJoin
  experiments; the file is retained as a dataset derivative.
- DesJoin contribution: Format conversion for the DesJoin experiments.
- Modified files: Yes. Original authorship and CC BY-SA 4.0 terms are
  retained; DesJoin modifications are also distributed under CC BY-SA 4.0.

## OpenData and WebTable

- Source project: https://github.com/BIT-DataLab/LakeBench
- Source version used: Not recorded in the supplied checkout.
- Source revision inspected for provenance: `8317cd57d25d2b533b9180fd6656d676144d4690` (repository HEAD dated 2025-05-25, inspected 2026-10-27).
- Date obtained: Not recorded in the supplied checkout.
- Source license: No explicit license identified in the LakeBench repository
  revision inspected.
- DesJoin files:
  - `Benchmarks/Revised/OpenData.csv`
  - `Benchmarks/Revised/WebTable.csv`
- Original LakeBench benchmark files redistributed: No. The original
  `OpenData.csv` and `WebTable.csv` files are not included.
- Transformation: DesJoin selection, revision, and annotation of
  table-column pairs, including joinability assessments where applicable.
  The revised files contain references and annotation decisions, not the
  underlying table contents.
- DesJoin contribution: Selection and review of table-column pairs and
  annotation decisions. No ownership is claimed over the underlying
  LakeBench data or identifiers.
- Underlying table contents redistributed: No.
