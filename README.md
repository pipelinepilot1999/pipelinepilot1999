# Sathvik Sai Appagana

**Bioinformatics Analyst / Computational Biologist** · MS Bioinformatics

🟢 Open to Bioinformatics Analyst, Computational Biologist, and Bioinformatics Scientist roles — especially at academic cancer centers.

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

### Supporting work
- [`multiomics-ml-brca`](https://github.com/pipelinepilot1999/multiomics-ml-brca) — Permutation-validated multi-omics ML for relapse (RNA-seq + DNA methylation, TCGA-BRCA); a 1,000× leak-free noise floor shows methylation adds no gain beyond expression — the measurement is the deliverable, not the direction.
- [`spatial-trimm-project`](https://github.com/pipelinepilot1999/spatial-trimm-project) — Spatial cell-motif discovery (TrimNN) with a permutation null correcting abundance bias, plus fixes for cell-type confounding and pseudoreplication.
- [`atac-seq-pipeline`](https://github.com/pipelinepilot1999/atac-seq-pipeline) — Differential chromatin accessibility (bowtie2 → MACS2 → DESeq2 → HOMER); independently recovers the FOXA1 pioneer factor as a positive control.
- [`gatk-somatic-variant-calling`](https://github.com/pipelinepilot1999/gatk-somatic-variant-calling) — GATK4 Best-Practices tumor–normal WES (hg38; bwa-mem2 → Mutect2 → Funcotator → maftools) on a real open-access patient case.

*Every repo ships a pinned conda environment, a data-download script, and a README that regenerates the figures — clone and run.*

## Tools
**Languages** — Python · R · Bash
**Single-cell & spatial** — Scanpy · Harmony · inferCNV · RCTD · SPOTlight · squidpy
**Bulk & epigenome** — STAR · featureCounts · DESeq2 · bowtie2 · MACS2 · HOMER · clusterProfiler
**Variants** — GATK4 · bwa-mem2 · Mutect2 · maftools
**ML & statistics** — scikit-learn · permutation testing · elastic-net / random forest · nested cross-validation
**Pipelines & infra** — Snakemake · SLURM · AWS EC2
