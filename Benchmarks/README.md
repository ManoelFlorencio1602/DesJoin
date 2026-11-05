# Benchmark data and licenses

## NextiaJD-S and NextiaJD-M

The original benchmarks were obtained from the NextiaJD repository:

https://github.com/dtak-upc/NextiaJD/tree/master/experiments

NextiaJD is distributed under the Apache License 2.0.
A copy of the license is provided in
[`LICENSES/Apache-2.0.txt`](../LICENSES/Apache-2.0.txt).

The files under `Benchmarks/Revised/` contain modifications and annotations
produced by the DesJoin authors. These files are derivative works and retain
the applicable Apache License 2.0 conditions.

The files related NextiaJD under `Benchmarks/Original/` are the original benchmark CSVs
published by the official NextiaJD GitHub repository and the one related to Spider is a set of table/column pairs derived from the Foreign Keys clauses contained in the schema definition from the Spider databases. The files under `Benchmarks/Revised/` are separately curated pair lists, rather than
row-for-row revisions of those original CSVs.

The revised NextiaJD and OpenData files contain manual review, corrections, and joinability
labels.

## Spider

The Spider dataset was introduced in:

Tao Yu et al. Spider: A Large-Scale Human-Labeled Dataset for Complex and
Cross-Domain Semantic Parsing and Text-to-SQL Task. EMNLP 2018.

Official resources:

- https://yale-lily.github.io/spider
- https://github.com/taoyds/spider
- https://huggingface.co/datasets/xlangai/spider

The Spider dataset is distributed under the Creative Commons
Attribution-ShareAlike 4.0 International license (CC BY-SA 4.0).
A copy of the license is provided in
[`LICENSES/CC-BY-SA-4.0.txt`](../LICENSES/CC-BY-SA-4.0.txt).

The file included in this repository was converted for use in the DesJoin
experiments. The original authorship and license remain unchanged.
Any DesJoin modifications to this material are also distributed under
CC BY-SA 4.0.

## OpenData and WebTable annotation sets

The OpenData and WebTable collections used as source material are associated
with the LakeBench project:

https://github.com/BIT-DataLab/LakeBench

The LakeBench repository does not currently provide an explicit license.
Consequently, this repository does not redistribute the original OpenData or
WebTable benchmark files.

The files under `Benchmarks/Revised/` contain annotation decisions produced
by the DesJoin authors. We record selected table-column pairs and
joinability assessments created during the DesJoin review process. Every pair
in `WebTable.csv` is positive: this is the final set after expansion of
non-transitive semantic joins. These files do not contain the underlying table contents.

References to table names, column names, and source identifiers are retained
solely to identify the objects evaluated during the annotation process.
No ownership is claimed over the underlying LakeBench data or identifiers.

The DesJoin license applies only to the original annotation decisions,
labels, documentation, and organization contributed by the DesJoin authors.
