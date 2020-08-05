---
layout: page
title: How To Use
permalink: /howto/
---

## Functions

### Drug Summary 
DrugBot allows users to submit a drug or small molecule of interest and outputs information pertaining to the search term. The **/drug** command provides a summary about the drug and links to various databases. 

The drug is searched through **DrugBank** and **L1000FWD** metadata. DrugBot will output links to drug landing pages for the drug based on which of these databases it is found in. 

✦ **Input Format:** `/drug <drug name>`

✦ **Example:** 
- Input: `/drug imatinib`
- Output: 
![image](/assets/images/drug_summary_output.png)

### Gene Enrichment Analysis
DrugBot allows users to submit a drug set for enrichment analysis. When users enter a drug set, the **/drugset** command can be used to trigger gene enrichment analysis to be performed. Users can upload a csv file with the drug set for analysis by calling **@drugbot**. Additionally, users can specify which gene-set library they want to be displayed in their results in Slack.

The drug set is analyzed using the **DrugEnrichr** API. The bot will output a link to **DrugEnrichr** for the drug set entered as well as summary statistics about the drug set. A bar graph displaying the top 10 enriched terms for the user selected gene-set library will attached as a pdf file. 

✦ **Input Format:** 
- Input (no library specified): 
    - `/drugset drug1, drug2, drug3... ` 
    - `/drugset drug1 drug2 drug3... ` 
- Input (library specified): 
    - `/drugset [library, drug1, drug2, drug3...] ` 
    - `/drugset [library, drug1 drug2 drug3...] ` 
        - Drug list can be space or comma separated.
        - Library specified input must be contained by brackets.
- Input (file upload): 
    - `@drugbot *file*` 
    - `@drugbot library *file*` 

✦ **Example:** 
- Input: `/drug DB *file*`
- Output: 
![image](/assets/images/drug_enrichment_output.png)

✦ **Gene Libraries:**
When specifying a library for output, DrugBot will recognize **DrugEnrichr** names or predefined short hands. DrugEnrichr names for libraries can be found [here](https://amp.pharm.mssm.edu/DrugEnrichr/#stats). Library short hands are available for most recent genesets for each database.
- Library short hands include:
    - GSA = Geneshot_Associated
    - GSPE = Geneshot_Predicted_Enrichr
    - DB = DrugBank_Small-molecule_Target
    - L1000D = L1000FWD_GO_Biological_Processes_Down
    - STITCH = STITCH_Target-seq_2015
    - SIDER = SIDER_Side_Effects

✦ **Help Commands:**
There are several built in help commands for performating enrichment analysis with GeneBot that can be called in Slack that provide concise summaries about different app features and functions. A list of all commands can be found by calling: `/drugset help?`

- `/drugset ?` → provides summary of how to use DrugBot for enrichment analysis  
- `/drugset library?` → provides instructions on how to specify library for output
- `/drugset fileupload?` → provides instructions on how to upload file for analysis
- `/drugset slashcommand?` → provides instructions on how to navigate /drugset command

For more details about workflow and data visualization analysis, check out the detailed user manual. 

Link to paper: 