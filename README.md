# Scorpion-SMR-eDNA-Metabarcoding
Code and Input Data for: eDNA metabarcoding as a biomonitoring tool for marine protected areas

**Manuscript is still undergoing peer-review at PlosOne**
Pre-print is available on [biorxiv](https://www.biorxiv.org/content/10.1101/2020.08.20.258889v1.full)


**Written by Zachary Gold**
**Manuscript Coauthors are Joshua Sprague, David J. Kushner, Erick Zerecero, and Paul H. Barber**

All code to run the [decontamination](https://github.com/zjgold/gruinard_decon)  and analysis are included. Data includes metadata files, raw [Anacapa](https://github.com/limey-bean/Anacapa) output file, generated intermediate files including figures, and supplemental tables. Raw sequencing data will be made available through a Dryad link in the manuscript upon publication.


## Decontamination
Decontamination was conducted using the gruinard_decon scripts modified to handle the presence of 2 separate sequencing projects. Negative and positive controls as well as all samples were included across both projects during the entire decontamination process. Data outputs from the MPA project were then separate post decontamination.

### Inputs
Inputs are located in the data directory

**Raw Anacapa Output** - fishcard_12S_all_ASV_raw_taxonomy_60_edited.txt
This file is a standard Anacapa output community-site table with columns of samples and rows of ASVs. See the Anacapa Github page linked above for a more detailed description of the bioinformatic processing.

**Metadata File** - mpa_metadata_02042020.txt
This file provides detailed information associated with each sample.

**Hash File**
This file links the updated taxonomy to each ASV. Taxonomic assignment was assigned to each ASV twice. First, using a reference database of only California fishes, [FishCARD](https://github.com/zjgold/FishCARD). Second, using a global reference database of all MiFish *12S* reference barcodes including marine mammals and birds. This updated taxonomy incorporates the marine mammal and bird assignments from the second round of taxonomic assignment to the first round of assignments. The first round of taxonomic assignments have empty strings given the lack of mammalian and avian reference barcodes in the fish only database. This 2 step taxonomic assignment procedure was done because previous work (See [FishCARD](https://authorea.com/doi/full/10.22541/au.159136805.55528691)) demonstrated that local reference databases provide higher accuracy in taxonomic assignments.

### Outputs

Outputs include the **ASV.nested** file which includes the raw ASV and read counts kept through each decontamination step, the **ASV.Summary** file which includes the counts of samples, ASVs, and reads retained at each step, the summarized .RDS and .CSV community-site tables, and general summary plots from the decontamination steps.

## Analysis

### Inputs
**post_occ_index** - post_occupancy_results_sum.taxonomy_tech_reps_summed_eDNA_index.RDS
This file is a community-site table with columns as samples and rows as species. ASVs assigned to the same taxonomic rank had reads summed together prior to eDNA index calculations. This table only includes ASVs that occurred after site occupancy modeling.

**post_occ_counts**  - post_occupancy_results_sum.taxonomy_tech_reps_summed_read_counts.RDS
This file is a community-site table with columns as samples and rows as species. ASVs assigned to the same taxonomic rank had reads summed together. This table only includes ASVs that occurred after site occupancy modeling.

**pre_index** - pre_occupancy_results_sum.taxonomy_tech_reps_summed_eDNA_index.RDS
This file is a community-site table with columns as samples and rows as species. ASVs assigned to the same taxonomic rank had reads summed together prior to eDNA index calculations. This table only includes ASVs retained after the first 2 steps of the decontamination pipeline.

**pre_counts** - pre_occupancy_results_sum.taxonomy_tech_reps_summed_read_counts.RDS
This file is a community-site table with columns as samples and rows as species. ASVs assigned to the same taxonomic rank had reads summed together. This table only includes ASVs retained after the first 2 steps of the decontamination pipeline.

**ASV.nested** - ASV.nested_final.RDS

**metadata** - mpa_metadata_02042020.txt

### Outputs

Outputs include figures included within the manuscript. Data tables and objects provide summaries of data included within the manuscript (i.e. number of ASVs, unique species found at each site, etc.)
