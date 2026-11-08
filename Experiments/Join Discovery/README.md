# Join Discovery experiments

This folder contains a notebook-based experiment for **table-oriented join
discovery**. It prepares table and column descriptions, predicts column types,
asks a language model which table pairs and columns are joinable, and compares
those predictions with benchmark ground truth.

The notebooks are intended to be run from this directory. They use relative
paths such as `NextiaJD-S/...`, and some of them set `project_dir` from the
current working directory.

## Notebooks and workflow

Run the notebooks in numerical order when producing a new experiment:

| Notebook | Purpose | Main input/output |
| --- | --- | --- |
| `01_Generate_Table_Description.ipynb` | Samples table contents and asks an LLM for a natural-language description of each table. | Reads CSVs from `<benchmark>/datasets/`; writes `table_descriptions.csv`. |
| `02_Generate_Column_Description.ipynb` | Generates a natural-language description for each column. | Reads CSVs from `<benchmark>/datasets/`; writes `column_descriptions.csv`. |
| `03_CTA_Prediction.ipynb` | Assigns a column type (CTA) to each described column using the categories in `cta_types.npy`. | Reads `column_descriptions.csv`; writes `column_descriptions_with_cta.csv` and a predicted CTA NumPy file in the selected benchmark directory. |
| `04_Generate_Table_JOIN_Prompts.ipynb` | Builds a prompt for each candidate table pair from the table and column descriptions. | Reads `table_descriptions.csv`, `column_descriptions.csv`, and `table_cartesians.csv`; writes `prompts/table_JD.json`. |
| `05_Inspect_prompt.ipynb` | Loads and displays generated prompts for inspection. | Reads `prompts/table_JD.json`. |
| `06_Predict_JD.ipynb` | Sends the table-pair prompts to a model and saves its joinability response for each pair. | Reads `prompts/table_JD.json` and `table_cartesians.csv`; writes raw model responses. |
| `07_Process_JD_output.ipynb` | Parses the raw JSON responses and expands predicted joinable column matches into rows. | Reads raw model results; writes `*_results_processed.csv`. |
| `08_Evaluating_Table_results.ipynb` | Evaluates predicted joinable table pairs against table-pair ground truth. | Reads `groundTruth.csv` and processed predictions; reports precision, recall, and F1. |
| `09_Evaluating_Column_results.ipynb` | Evaluates predicted joinable column pairs against column-pair ground truth. | Reads `groundTruth.csv` and processed predictions; reports precision, recall, and F1. |

The first three notebooks generate table/column metadata; notebooks 4–6 create
and run the join-discovery prompts; notebook 7 converts model output into a
normalized prediction table; and notebooks 8–9 evaluate table-level and
column-level predictions. Notebooks 8 and 9 include benchmark-specific
ground-truth handling; for NextiaJD, the notebook code can restrict the
evaluation to `JOINABLE_LEVEL == 5`.

## Files and benchmark folders

Each benchmark folder follows the same general layout:

```text
<benchmark>/
├── datasets/                         # Source CSV tables used to generate descriptions
├── prompts/                          # Generated prompt JSON (table_JD.json)
├── output/                           # Raw and processed model results
├── filenames.txt                     # Table names in the benchmark
├── groundTruth.csv                   # Human/benchmark joinability annotations
├── table_cartesians.csv              # Candidate table pairs for prediction
├── table_descriptions.csv            # Generated table descriptions
├── column_descriptions.csv           # Generated column descriptions
└── column_descriptions_with_cta.csv  # Column descriptions plus predicted CTA
```

The exact ground-truth columns differ by benchmark. For example, NextiaJD files
include table and column pair annotations and `JOINABLE_LEVEL`; Spider,
OpenData, and WebTable use their own table/column naming conventions. The
NextiaJD folders also contain `datasetInformation_testbedS.csv` or
`datasetInformation_testbedM.csv`, which record source-file metadata such as
delimiters, file sizes, and provenance.

Files shared by the experiment notebooks:

| File | Role |
| --- | --- |
| `cta_types.npy` | CTA label vocabulary loaded by notebook 3. |
| `filenames.txt` (per benchmark) | Inventory of source table names. |
| `groundTruth.csv` (per benchmark) | Reference labels used by evaluation notebooks. |
| `table_cartesians.csv` (per benchmark) | Table pairs to be scored. |
| `table_descriptions.csv` (per benchmark) | Table-level language descriptions used to build join prompts. |
| `column_descriptions.csv` (per benchmark) | Column-level language descriptions used to build join prompts. |
| `column_descriptions_with_cta.csv` (per benchmark) | Column descriptions enriched with a CTA label. |
| `prompts/table_JD.json` (per benchmark) | Serialized prompts keyed by target and candidate table. |
| `output/<model>_results.csv` (per benchmark) | Raw LLM responses, including the response JSON and table-pair identifiers. |
| `output/<model>_results_processed.csv` (per benchmark) | Normalized joinable table/column pairs with `ds_name`, `ds_name_2`, `left_column`, and `right_column`. |

In the current checkout, the `datasets/` and `prompts/` directories are empty;
the notebooks expect source CSVs and generated prompt JSON to be present before
the corresponding steps can run. Existing description, ground-truth, and
result CSVs are benchmark artifacts rather than replacements for the source
tables.

## Running the experiment

1. Open this directory as the working folder in Jupyter or VS Code.
2. Obtain the source CSVs for the benchmark and place them in its `datasets/`
   directory. Keep filenames consistent with `filenames.txt`,
   `table_cartesians.csv`, and `groundTruth.csv`.
3. Configure API credentials for the notebooks that call a model. Notebooks
   1–3 use the OpenAI Python client; notebook 6 reads `OPENROUTER_API` from a
   `.env` file in this directory. Do not commit API keys.
4. In each notebook, set `BENCHMARK` to the same benchmark folder. Generate
   descriptions and CTA labels, generate and inspect prompts, run predictions,
   process the results, then evaluate them.

The notebooks use Python packages including `pandas`, `numpy`, `openai`,
`tenacity`, `tqdm`, `requests`, and `python-dotenv`. A Jupyter environment is
also required. This experiment folder does not define a pinned dependency
file, so package versions may need to be selected to match the notebook code
and API provider.

### Important result-path setting

The checked-in result files and notebooks 7–9 use the singular directory
`<benchmark>/output/`. Notebook 6 currently sets its raw output path to
`<benchmark>/outputs/` (plural). Before running the full workflow, change that
notebook's output path to `output/`, or otherwise make the raw results
available at the path expected by notebook 7. Also set the same `BENCHMARK`
and model name consistently in notebooks 6–9.

## Relationship to the repository

This directory is an experiment workspace, separate from the repository's
published benchmark definitions. Consult the repository
[README](../../README.md), [data provenance notes](../../DATA_PROVENANCE.md),
and [benchmark documentation](../../Benchmarks/README.md) for benchmark
availability, attribution, and licensing information. In particular, some
underlying source collections are not redistributed here; researchers must
obtain them from their providers.
