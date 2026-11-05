# DesJoin
Files used in "DesJoin: Table-Oriented Semantic Join Discovery with LLM-Based Descriptions" paper, including Original and Revised benchmarks and Annotation guidelines.

> [!IMPORTANT]
> This repository is publicly available for peer review and artifact
> evaluation. It contains original DesJoin contributions and components
> derived from third-party benchmarks. No single license applies to the
> entire repository.
>
> See [DATA_PROVENANCE.md](DATA_PROVENANCE.md),
> [Benchmarks/README.md](Benchmarks/README.md), and
> [LICENSES/](LICENSES/) for the applicable terms and attribution notices.

## Benchmark availability

This repository does not redistribute the original OpenData and WebTable
benchmark files associated with LakeBench because no explicit redistribution
license was identified.

The repository provides only the annotation decisions and revised benchmark
definitions created by the DesJoin authors. Researchers are responsible for
obtaining the underlying source collections from their respective providers.

Every pair in `Benchmarks/Revised/WebTable.csv` is positive (joinable). This
file is the final set after expansion of non-transitive semantic joins, so it
intentionally has no label column.

Original or derived materials from NextiaJD and Spider are distributed under
their respective Apache-2.0 and CC BY-SA 4.0 terms.
