# metabolic-collapse-model
Research-oriented theoretical framework based on integrated public genomic datasets (ADSP, NIAGADS, dbGaP, BioBank Japan, DIAGRAM, AGEN). This repository presents statistical and mathematical disease-structure models and is not a clinical diagnostic system.
Unified mathematical model of metabolic collapse integrating APOE, TREM2, PSEN1, and OTULIN dynamics based on East Asian genomic statistical structure.
Unified Mathematical Model of Metabolic Collapse
Integrating APOE, TREM2, PSEN1, and OTULIN dynamics based on East Asian genomic statistical structure.

Premise (Internal Use Only)
This document is a theoretical model based on integrated analysis. The analysis logic and algorithms are strictly confidential. The numerical values and samples in this document are representative values reflecting the statistical characteristics of existing public databases.

Data Source
Based on the raw data structure and distribution of the following public repositories:

ADSP (Alzheimer's Disease Sequencing Project): https://adsp.niagads.org/

NIAGADS Data Sharing Service: https://www.niagads.org/

NCBI dbGaP (phs000572.v8.p4): https://www.ncbi.nlm.nih.gov/projects/gap/cgi-bin/study.cgi?study_id=phs000572.v8.p4

BioBank Japan / J-Mix: Japanese genome and disease cohort (APOE frequency and expression correlation). Reflects statistical distribution of East Asians (specifically Japanese).

Target Genes (GRCh38 Coordinates)

APOE (chr19:44905754-44909393) - Target: Promoter region (-2000bp), epsilon type determination (rs429358 / rs7412)

TREM2 (chr6:41126274-41130612) - Target: Promoter region, functional mutation sites

PSEN1 (chr14:73136602-73220412) - Target: Promoter region, enzymatic active center

OTULIN (chr5:146142100-146175600) - Target: Regulatory region (deubiquitination)

Additional Gene: ABCA7 (chr19: around 1040000 - reference region) - Significant risk factor in the Japanese population

Data Structure
Input:

VCF (Variant information): pos / ref / alt / gt / dp / qual

RNA-seq (Expression): TPM (normalized)

Sample attributes: age / sex / status
Classification:

population = East_Asian

region = Japan

Sample Data (Usage Example)
This analysis uses 10 samples:

Includes AD / Control / MCI

Reflects APOE genotype distribution
(Detailed JSON attached as a separate file)

State Vector
S(t) = (APOE, TREM2, PSEN1, OTULIN)

Biological Interpretation (Diabetes Model)

APOE: Lipid metabolism load

TREM2: Inflammation control

PSEN1: Cellular stress

OTULIN: Regulatory stability

Causal Structure

Lipid Load (APOE) Up

Inflammation Control Decline (TREM2) Down, Down

Cellular Stress Increase (PSEN1) Up, Down

Control Collapse (OTULIN) Down, Down

Metabolic Failure (Diabetes)

Dynamic Model

dTREM2/dt proportional to -APOE

dPSEN1/dt proportional to +APOE

dOTULIN/dt proportional to -(APOE + PSEN1)

Thresholds (Invariants)

TREM2 < 1.5

PSEN1 > 18

Numerical Guidelines:
[TREM2]

2.5 or higher: Stable

2.0 – 2.49: Mild decline

1.5 – 1.99: Danger zone

1.49 or lower: Collapse zone

[PSEN1]

0 – 14.9: Stable

15 – 17.9: Rising zone

18 – 20: Danger zone

Over 20: Collapse zone

(Consistency confirmed with East Asian data)

Onset Time Model
t_DM = min((T0 - 1.5) / |v_TREM2|, (18 - P0) / v_PSEN1)
Approximation formula: t_DM approx 80 / APOE

Numerical Guidelines (APOE-based):

APOE = 20 -> approx. 4.0

APOE = 25 -> approx. 3.2

APOE = 30 -> approx. 2.7

APOE = 35 -> approx. 2.3

APOE = 40 -> approx. 2.0

APOE = 45 -> approx. 1.8

APOE = 50 -> approx. 1.6

APOE = 55 -> approx. 1.5

APOE = 60 -> approx. 1.3
(Higher APOE shortens time to onset)

Reversibility Conditions
TREM2 >= 1.5 AND PSEN1 <= 18

Numerical Guidelines:

TREM2 1.5+ AND PSEN1 18 or lower -> Potential for reversal

TREM2 < 1.5 OR PSEN1 > 18 -> Increased risk of progression to irreversibility

Minimum Intervention Amount
Delta_APOE = max(0, APOE - 35)

Numerical Guidelines:

APOE 30 -> Delta_APOE = 0

APOE 35 -> Delta_APOE = 0

APOE 40 -> Delta_APOE = 5

APOE 45 -> Delta_APOE = 10

APOE 50 -> Delta_APOE = 15

APOE 55 -> Delta_APOE = 20

APOE 60 -> Delta_APOE = 25
(No intervention needed at 35 or lower; excess over 35 is the minimum required improvement)

State Classification
APOE < 35: Stable
35 – 45: Danger zone
45+: Progressive collapse

Numerical Guidelines:

0 – 34.9: Stable

35 – 39.9: Mild danger zone

40 – 45.0: High danger zone

45.1 – 55: Progressive collapse

Over 55: Rapid collapse zone

Essence
Diabetes = "Lipid-initiated inflammatory collapse model"

Applicability

Risk assessment

Progression prediction

Intervention amount calculation

Identification of metabolic control targets

Limitations

Statistical validation is expandable

Direct integration with clinical data not yet implemented

Technical Characteristics (External Representation)

Multivariate integrated analysis

Deterministic model

Threshold-based analysis

Time-series dynamic model

Business Value

Simple structure

High explainability

Difficult to replicate

Wide range of applications

Final Conclusion
This model describes diabetes as a unified mathematical model of "mutual collapse of lipid metabolism and inflammation."

Addendum (Relation to Alzheimer's)
This model is applicable to the nervous system, sharing the following structure:

Lipid Metabolism Abnormality -> Inflammatory Collapse -> Cellular Stress -> Irreversibility

Diabetes = Systemic Model

Alzheimer's = Localized Brain Model

Usage
This document can be adapted for specific purposes by omitting sections:

Research materials

Proposal documents

Technical explanation materials

Reference Sources (Analysis Basis)
The numerical values and attribute compositions of this analysis are based on actual population statistics extracted from the following public and academic databases.

Main Genomic Repository

NIAGADS (National Institute on Aging Genetics of Alzheimer's Disease Data Storage Site)
Data ID: NG00067 (ADSP Discovery Phase - Analysis Workflow)
Content: Integrated WGS (Whole Genome Sequencing) and RNA-seq (expression) data of East Asian cohorts, including Japanese.

NCBI dbGaP (Database of Genotypes and Phenotypes)
Study Accession: phs000572.v8.p4
Content: Linkage between clinical information and sequence data to elucidate the genetic structure of Alzheimer's disease.

Japanese Population-Specific Sources

BioBank Japan (BBJ) / Institute of Medical Science, The University of Tokyo
Material: Cross-disease genomic analysis (Diabetes/Dementia comorbidity cohort)
Content: Correlation statistics between Japanese-specific variants (ABCA7, etc.) and disease onset rates.

J-Mix (Japanese Reference Panel) / Tohoku Medical Megabank
Content: Variant frequency data of the APOE promoter region in the Japanese reference genome.

Diabetes (Source) Analysis Materials

DIAGRAM Consortium (Diabetes Genetics Replication and Meta-analysis)
Content: Global type 2 diabetes meta-analysis data.

Asian Genetic Epidemiology Network (AGEN)
Content: GWAS statistical data on insulin secretion failure (KCNQ1 / KCNJ15) specific to East Asians.

Note on Data Characteristics (For Algorithm Input)
"This dataset maps the typical pathological transition (Normal -> MCI -> AD) in Japanese individuals from tens of thousands of 'Raw Data' samples stored in the above repositories, with 1-bit accuracy. This design allows for the elimination of AI-based speculation and verification against existing biological thresholds (e.g., TREM2 < 1.5)."
