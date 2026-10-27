# Annotation Guidelines for Joinability Categories

## 1. Objective

The objective of the annotation is to determine the **semantic relationship between a pair of columns from two tables** and classify the pair according to categories **C1–C6**.

Annotators should consider:

- the meaning of the two tables;
- the meaning and role of the selected columns;
- whether the columns encode the same information;
- whether their value domains support a meaningful join; and
- whether the observed relationship is genuinely pairwise or results from a non-transitive relationship.

The annotation should be based on **semantic meaning**, rather than on value overlap alone.

---

## 2. Annotation Procedure

For each candidate pair of columns:

1. **Inspect both tables** to understand the real-world concepts they describe.
2. **Inspect the selected columns** and determine what information each column represents.
3. Determine whether the tables describe related concepts.
4. Determine whether the selected columns represent compatible information.
5. Determine whether a join between the columns would be semantically meaningful.
6. If the pair appears to be negative, determine which source of semantic noise best explains it.
7. Assign exactly **one category from C1–C5** according to the rules below.

> **Important:** Numeric, textual, or categorical value overlap by itself is not sufficient evidence that two columns are joinable.

---

# 3. Category Definitions

## C1 — No Table Correlation

### Definition

Assign **C1** when the two tables describe **unrelated real-world concepts**.

Any observed overlap between their values is considered **coincidental** and does not represent a meaningful semantic relationship.

### Annotation rule

Use C1 when:

- the tables concern fundamentally unrelated entities or concepts; and
- there is no meaningful relationship between the information represented by the tables.

### Example

```text
IPODatFull.USACompany × water-hydrants.COMPRESSION
```

Even if both columns contain overlapping numeric values, the overlap is not semantically meaningful.

### Decision rule

> **If the tables themselves are unrelated, assign C1.**

---

## C2 — Tables Correlate, but Not Columns

### Definition

Assign **C2** when the two tables refer to **related entities or concepts**, but the selected columns represent **different roles, attributes, or events** that cannot be meaningfully aligned.

### Annotation rule

Use C2 when:

- the tables are semantically related; but
- the selected columns describe different aspects of those tables; and
- the columns cannot be meaningfully joined despite the relationship between the tables.

### Example

```text
host_since × first_review
```

Both columns occur in Airbnb-related information, but:

- `host_since` represents the host's registration date;
- `first_review` represents the first guest interaction/review.

They therefore represent different events.

### Decision rule

> **If the tables are related but the selected columns have incompatible semantic roles, assign C2.**

---

## C3 — Superficially Similar Columns

### Definition

Assign **C3** when the columns appear similar at a **surface level**, but represent **distinct underlying concepts**.

Similarity may arise from:

- the same data type;
- the same format;
- similar column names;
- similar-looking values; or
- another superficial characteristic.

### Annotation rule

Use C3 when:

- the columns have apparent structural or lexical similarity; but
- their underlying meanings are different.

### Example

```text
date_of_birth × DispositionDate
```

Both columns contain dates, but:

- `date_of_birth` represents a person's birth date;
- `DispositionDate` represents a process outcome date.

The common data type does not imply joinability.

### Decision rule

> **If the columns look similar but represent different concepts, assign C3.**

---

## C4 — Same Semantics, Non-Joinable Domains

### Definition

Assign **C4** when the two columns represent the **same conceptual attribute**, but their **value domains or descriptions do not support a meaningful join**.

This category is important because semantic similarity alone does not guarantee joinability.

### Annotation rule

Use C4 when:

- the columns represent the same conceptual attribute; but
- their possible values, representations, or domains are incompatible for a meaningful join.

### Examples

```text
sex_upon_intake × sex_upon_outcome
```

The columns concern the same conceptual attribute, but represent different points/states and therefore do not constitute a meaningful join.

Another example:

```text
Kidney Disease
```

A binary presence indicator and a numeric severity measure may both concern kidney disease, but their domains are not directly joinable.

### Decision rule

> **If the columns mean the same thing conceptually but their domains do not support a meaningful join, assign C4.**

---

## C5 — Same Semantics, Joinable Domains

### Definition

Assign **C5** when the two tables and columns encode the **same information** and the selected columns represent **joinable information**.

This is the **validated positive** category.

### Annotation rule

Use C5 when:

- the tables provide compatible semantic context;
- the columns represent the same information or concept; and
- their value domains support a meaningful join.

### Examples

```text
mapcountry × country_of_citizenship
```

Both columns represent the country associated with a person/company context and their domains support a meaningful join.

Another example:

```text
Province × Canada
```

where the column represents the province in which an organization is located.

### Decision rule

> **If the columns encode the same information and their domains support a meaningful semantic join, assign C5.**

---

# 4. Recommended Decision Hierarchy

To improve consistency between annotators, apply the categories in the following order:

```text
Are the tables unrelated?
   └── Yes → C1
   └── No → Are the tables related, but do the selected columns represent
   different roles, attributes, or events?
      └── Yes → C2
      └── No → Do the columns only appear similar because of their
   format, data type, name, or surface characteristics?
         └── Yes → C3
         └── No → Do the columns represent the same conceptual attribute,
   but have incompatible/non-joinable domains?
            └── Yes → C4
            └── No  → C5
```

### Important distinction

The most important distinction for annotation is:

**Semantic similarity ≠ joinability.**

In particular:

```text
C3 → similar, different meaning
C4 → same meaning, but non-joinable domains
C5 → same meaning and joinable domains
```

---

# 5. Evidence to Consider

Annotators should prioritize semantic evidence from:

1. **Table context** — what real-world entity or concept does the table describe?
2. **Column meaning** — what does the column actually represent?
3. **Column role** — what role does the attribute play within its table?
4. **Value domain** — what kinds of values can occur in the column?
5. **Relationship between domains** — can values from one domain meaningfully correspond to values from the other?
6. **Pairwise relationship** — does the relationship hold directly between the two tables?

Value overlap should be treated as **supporting evidence**, not as sufficient evidence by itself.

---

# 6. Annotation Output

For every candidate pair, record:

| Field | Description |
|---|---|
| `table_1` | First table |
| `column_1` | Selected column from the first table |
| `table_2` | Second table |
| `column_2` | Selected column from the second table |
| `category` | One of `1`, `2`, `3`, `4`, `5`|

---

# 7. Positive Benchmark Label

For benchmark construction, **C5 represents the validated joinable pairs**.

Therefore:

```text
Positive / Joinable → C5
Negative / Not directly joinable → C1, C2, C3, C4
```
