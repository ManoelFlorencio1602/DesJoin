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

Changes made by the DesJoin authors are documented in this repository and in
the accompanying paper.

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
by the DesJoin authors. They record selected table-column pairs and, where
applicable, joinability assessments created during the DesJoin review
process. They do not contain the underlying table contents.

References to table names, column names, and source identifiers are retained
solely to identify the objects evaluated during the annotation process.
No ownership is claimed over the underlying LakeBench data or identifiers.

The DesJoin license applies only to the original annotation decisions,
labels, documentation, and organization contributed by the DesJoin authors.
