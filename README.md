# Sathvik Sai Appagana

**Bioinformatics Analyst / Computational Biologist** · MS Bioinformatics

Open to Bioinformatics Analyst, Computational Biologist, and Bioinformatics Scientist roles — especially at academic cancer centers.

📧 sathvikappagana@gmail.com · [LinkedIn](https://linkedin.com/in/sathvik-appagana)

---

I build reproducible, defensible bioinformatics pipelines — each validated against known biology as a positive control, honest about where methods fail instead of smoothing it over, and treating a well-measured null result as a real finding.

## Breast cancer, at three resolutions

My core work is one connected story, deliberately built so each project answers what the previous one couldn't:

- **Bulk RNA-seq** found the ER+/TNBC subtype signature by averaging across all cells.
- **Single-cell** localized that signature to the malignant epithelial compartment and proved malignancy cell-by-cell via copy-number inference.
- **Spatial deconvolution** put the compartments back into tissue, showing the tumor–immune architecture itself differs by subtype — TNBC infiltrated, ER+ excluded.

### Core arc
- [`rnaseq-brca-pipeline`](https://github.com/pipelinepilot1999/rnaseq-brca-pipeline) — Bulk RNA-seq of BRCA subtypes (STAR → featureCounts → DESeq2 → clusterProfiler); recovers canonical ER+/TNBC signatures in the correct direction.
- [`scrna-tme-pipeline`](https://github.com/pipelinepilot1999/scrna-tme-pipeline) — scRNA-seq of the tumor microenvironment (31,265 cells; Scanpy/Harmony); inferCNV confirms malignancy cell-by-cell.
- [`spatial-tme-pipeline`](https://github.com/pipelinepilot1999/spatial-tme-pipeline) — Reference-based spatial deconvolution (RCTD/SPOTlight) across 6 Visium sections, validated against pathologist annotation.

## Measuring what methods actually add

A second body of work asks a harder question than "does the pipeline run?" — **does the method deliver what it claims, compared against the simplest honest baseline?** In each project, the evaluation is the deliverable.

- [`brca-multiomics-relapse-benchmark`](https://github.com/pipelinepilot1999/brca-multiomics-relapse-benchmark) — Does multi-omics beat clinical staging for breast cancer relapse? **No.** On identical 50-fold nested CV (TCGA-BRCA, n=367), a clinical-only model (AUC 0.779) beats XGBoost on 19,338 omics features (0.669) and a pathway-informed neural network (0.613); a 7-block ablation shows methylation adds nothing over expression. A 9-gene panel with a frozen cutpoint still replicates in METABRIC (n=1,902; RR 1.95, p=1.2×10⁻⁵). Includes a denoising multi-modal autoencoder with a fold-safe transduction check. Docker + Nextflow DSL2.
- [`rare-disease-acmg-benchmark`](https://github.com/pipelinepilot1999/rare-disease-acmg-benchmark) — How much of automated rare-disease variant interpretation is database lookup rather than reasoning? Every result is a paired informed-vs-blinded delta. A ClinVar lookup that reasons about nothing matches ClinGen expert panels on 97.5% of variants; a guideline-compliant ACMG/AMP engine reaches 36.4%; the ceiling for *any* automated classifier is 51.1%. Exomiser prioritization on real phenopacket cases injected into the GIAB trio.
- [`civic-rag-eval`](https://github.com/pipelinepilot1999/civic-rag-eval) — RAG for somatic variant interpretation over CIViC, with negative controls and baselines the model has to beat. Finding: **retrieval causes confabulation** — with no context the model abstains; with retrieved evidence it invents clinical significance for 22.7% of plausible variants that have no CIViC record. A structured lookup beats embeddings on recall@1 (0.960 vs 0.366).
- [`longread-platform-benchmark`](https://github.com/pipelinepilot1999/longread-platform-benchmark) — Oxford Nanopore vs PacBio HiFi on HG002 chr20 at matched 49.6× coverage against GIAB truth. SV accuracy is near-identical (F1 0.81 vs 0.79); the platforms separate on indels (HiFi F1 0.87 vs ONT 0.75) and phasing (ONT 2.1 Mb vs 0.53 Mb blocks). ONT phased methylation recovers imprinting at known chr20 DMRs. Nextflow DSL2, pinned containers.

## Pipelines & data engineering

- [`atac-seq-pipeline`](https://github.com/pipelinepilot1999/atac-seq-pipeline) — Differential chromatin accessibility (bowtie2 → MACS2 → DESeq2 → HOMER); independently recovers the FOXA1 pioneer factor as a positive control.
- [`gatk-somatic-variant-calling`](https://github.com/pipelinepilot1999/gatk-somatic-variant-calling) — GATK4 Best-Practices tumor–normal WES (hg38; bwa-mem2 → Mutect2 → Funcotator → maftools) on a real open-access patient case.
- [`tcga-brca-postgres`](https://github.com/pipelinepilot1999/tcga-brca-postgres) — Normalized PostgreSQL 16 database over TCGA-BRCA clinical, somatic mutation and RNA-seq data (25M rows, 6 tables, 40 enforced constraints, 57 tests). A data-quality audit found only 791 of 1,247 samples were exome-sequenced — the correct denominator moves TP53 from 21.2% to a published-range 33.4%. Index analysis with `EXPLAIN ANALYZE`: one query 574 → 6 ms, and three of five needed no index.

*Every repo ships a pinned environment (conda or Docker), a data-download script, and a README whose numbers are regenerated from its own results.*

## Tools

**Languages** — Python · R · Bash · SQL

**Single-cell & spatial** — Scanpy · Harmony · inferCNV · RCTD · SPOTlight · squidpy

**Bulk & epigenome** — STAR · featureCounts · DESeq2 · bowtie2 · MACS2 · HOMER · clusterProfiler · modkit

**Variants & long reads** — GATK4 · bwa-mem2 · Mutect2 · maftools · minimap2 · Sniffles2 · cuteSV · Truvari · Clair3 · WhatsHap · hap.py

**Clinical interpretation** — ACMG/AMP criteria · Exomiser · ClinVar · ClinGen · CIViC · gnomAD

**ML & statistics** — scikit-learn · XGBoost · autoencoders · nested cross-validation · permutation testing · survival (Kaplan–Meier, log-rank)

**Data & infra** — PostgreSQL · Nextflow DSL2 · Snakemake · Docker · SLURM · AWS EC2
