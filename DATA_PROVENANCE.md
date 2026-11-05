# Data provenance

This document describes the provenance of the datasets used in the DesJoin
experiments. It records the original data sources, versions and acquisition
dates, applicable licenses, transformations, and contributions made during
the preparation of the experimental benchmarks.

The document covers the following datasets:

- **NextiaJD-S and NextiaJD-M:** Original benchmarks and manually reviewed
  revised versions.
- **Spider:** Original benchmark converted to the format required by DesJoin.
- **OpenData and WebTable:** Selected and revised table-column pairs derived
  from the LakeBench project.

For each dataset, we distinguish between the original source material and
the modifications introduced by DesJoin. These modifications may include
format conversion, selection, manual review, corrections, and joinability
annotations.

The provenance information is provided to support transparency,
reproducibility, and appropriate attribution. Redistribution and licensing
conditions are documented individually for each dataset. DesJoin contributions
should not be interpreted as ownership of the underlying datasets or their
original contents.

## NextiaJD-S and NextiaJD-M

- Source: https://github.com/dtak-upc/NextiaJD/tree/master/experiments
- Source version used: The original files in this repository are
  the original benchmark CSVs published in the official NextiaJD
  GitHub repository.
- Date obtained:
  - NextiaJD-S: 2025-04-25.
  - NextiaJD-M: 2025-05-12.
- Source license: Apache License 2.0.
- DesJoin files:
  - `Benchmarks/Original/NextiaJD-S.csv`
  - `Benchmarks/Original/NextiaJD-M.csv`
  - `Benchmarks/Revised/NextiaJD-S.csv`
  - `Benchmarks/Revised/NextiaJD-M.csv`
- Transformation: The `Original/` files are the original CSVs from the
  official NextiaJD GitHub repository; The `Revised/` files are separate, manually
  reviewed pair lists with corrections and joinability annotations. They are
  modified derivatives and are not row-for-row transformations of the current
  original CSVs.
- DesJoin contributions: The revised files contain manual review,
  corrections, and joinability labels.

## Spider

- Source: https://yale-lily.github.io/spider
- Additional sources:
  - https://github.com/taoyds/spider
  - https://huggingface.co/datasets/xlangai/spider
- Date obtained: 16/06/2025.
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
- Source version used: The original files in this repository are
  the original benchmark CSVs published in the official LakeBench
  GitHub repository.
- Date obtained:
  - OpenData: 22/11/2025.
  - WewbTable: 29/05/2025.
- Source license: No explicit license identified in the LakeBench repository
  revision inspected.
- DesJoin files:
  - `Benchmarks/Revised/OpenData.csv`
  - `Benchmarks/Revised/WebTable.csv`
- Original LakeBench benchmark files redistributed: No. The original
  `OpenData.csv` and `WebTable.csv` files are not included.
- Transformation: DesJoin selection, revision, and annotation of
  table-column pairs. OpenData includes joinability assessments. WebTable
  contains positive pairs only: it is the final set after expansion of
  non-transitive semantic joins, so no label column is included. The revised
  files contain references and annotation decisions, not the underlying
  table contents.
- DesJoin contribution: Selection and review of table-column pairs and
  annotation decisions. No ownership is claimed over the underlying
  LakeBench data or identifiers.
- Underlying table contents redistributed: No.
