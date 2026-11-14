# Evidence and evaluation scope

The case study draws on the authored paper, retained notebook source and outputs, supporting report, and dataset archive. It distinguishes those records from a fresh reproduction or a field deployment.

## Available evidence

| Artifact | What it supports |
| --- | --- |
| Executed notebook with saved output | Historical preprocessing, classifier metrics, contamination comparisons, and uncertainty summaries |
| Authored paper in PDF and Word formats | The author's framework, methodology, discussion, and interpretation |
| Supporting report | Earlier literature review and proposed design |
| UCI dataset copy | The underlying household consumption measurements |
| Local Merkle implementation | Membership-proof and integrity-check behavior |

The notebook records writing result CSVs, a summary JSON, and figures, but standalone exported result files are not present in the supplied folder. The public table is transcribed from saved text output.

## Archival checks

- The implementation notebook and its demo copy are byte-identical.
- All 33 ordinary Python code cells passed syntax parsing; one package-installation cell was excluded.
- No saved error output was present.
- Thirty-four isolated assertions passed for synthetic Merkle membership and altered-leaf rejection, including odd-sized trees.
- Dataset ZIP and Word-document containers passed integrity checks.
- The large demo dataset text matches the dataset ZIP's contents by SHA-256.

No full notebook run, model retraining, live IoT collection, blockchain transaction, or deployment test was performed for the case study.

## Interpreting reported gains

The saved results show partial benefits in some conditions. They do not show uniform superiority. For example, the 20% gradual condition has better recall and F1 for ChainGuard, but the complete table also contains low-contamination cases where its recall is below the comparison conditions.

At severe contamination, all approaches lose substantial detection capability. A result near the majority-class accuracy should not be interpreted as a reliable detector.

The ChainGuard condition retains additional reference examples, while the filter selects random sample subsets. A controlled ablation is needed to isolate the contribution of reference retention, sample filtering, and provenance verification.

## Important evaluation boundaries

**Synthetic labels:** The source dataset does not contain verified theft outcomes. Generalization to operational theft detection remains to be evaluated.

**Temporal dependence:** Rolling features are constructed before a random train/test split. Time-series-aware validation is needed to assess the effect of related neighboring observations across partitions.

**Calibration:** Calibration examples are drawn from the original training pool, rather than a clearly independent held-out calibration partition. Formal uncertainty-coverage conclusions need stronger experimental separation.

**Early warning:** The monitor is inspected on test predictions after model training. This does not demonstrate a measured lead time before degradation in a chronological deployment.

**Cryptographic scope:** Local commitment checks establish integrity relative to a reference, not sensor authenticity, clean labels, or successful live-chain anchoring.

**Cost model:** Reduced transaction counts and assumed per-transaction fees are estimates, not realized network savings.

## Next evaluation steps

Useful follow-up work would separate chronological training, calibration, and testing; hold reference conditions constant across ablations; report uncertainty across runs; retain per-run result artifacts; and validate the proposed anchoring workflow with transaction evidence. Any deployment claim would also require tests against a defined sensor and adversary model.
