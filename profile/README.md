# Mason Lab bioinformatics projects guide

## Introduction 

### Mason-Lab-Code GitHub organization

The Mason-Lab-Code GitHub organization is a centralised store of all of our code.  
Scripts are organised into workflows. Each workflow has its own repository, containing all of the scripts required to run the workflow. Repositories also contain a README file, detailing the function of each script, all software requirements, links to any reference files needed, a workflow overview diagram, and instructions on how to implement the workflow. (GitHub account with Mason-Lab-Code membership required to view repositories.)  

### Viking group space (biol-cancerinf-2020) 

Path to Mason Lab group space on Viking: /mnt/scratch/project/biol-cancerinf-2020/  
This directory has centralised locations for our raw data, reference data, and code (synced with Mason-Lab-Code GitHub).  
biol-cancerinf-2020 directory structure:  
  
![image](https://github.com/Mason-Lab-Code/.github/assets/73953685/bf5dcd2b-4e95-4629-b31a-131fa7eadd78)

## Getting started 

### Viking account

If you haven't already, complete the [Viking user application form](https://docs.google.com/forms/d/e/1FAIpQLSfXkL10ypU6EQCBB2jS5oDwTpRMo77ppl7dvdbLnXm5zrKR7Q/viewform) to request a Viking account.  
Enter the Viking project code: **biol-cancerinf-2020**

### Using Viking

Viking is the University of York's high-performance computing (HPC) cluster. It has enough storage, memory and computing resources to carry out our bioinformatics projects. The [Viking documentation](https://vikingdocs.york.ac.uk/index.html) explains how to access and use Viking. 

Viking uses the Unix/Linux operating system. If you haven't used Linux before, you can read the (Linux shell)[https://vikingdocs.york.ac.uk/beginners_guide/linux_shell.html] section of the Viking documentation. 

Make sure you are comfortable using basic Linux commands, logging in to Viking, submitting batch jobs, and running interactive sessions. 

### Git and GitHub

If you are unfamiliar with Git and GitHub, try watching these introductory videos: 
* [*How to use GitHub*](https://www.youtube.com/watch?v=PQsJR8ci3J0)
* [*Git, GitHub, and GitHub Desktop for beginners*](https://www.youtube.com/watch?v=8Dd7KRpKeaE)

### GitHub account

If you don't already have a GitHub account, create one. Click *Sign Up* in the top right corner. 

### Membership

Once you have a GitHub account, ask Richard or Andrew to add you as a member of the Mason-Lab-Code organization. This will give you access to all of our code repositories.  

### Personal access token

* To create a personal access token, follow the [instructions](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).  
* Select "Tokens (classic)", not "Fine-grained tokens".  
* When selecting scopes/permissions, tick "repo".  
* Make a note of your personal access token.  
* Every time Git prompts you for a "password" on the command line, enter your personal access token (not the password for your GitHub account).  

## Executing a new project on Viking

### Naming system for files and directories

Project directories (inside biol-cancerinf-2020/Projects/)  
* YYYYMMDD-INITIALS-Project_name
* e.g. 20231006-RG-ATACseq_Bladder_vs_Ureter

Raw data directories (inside biol-cancerinf-2020/Raw-Data/)  
* YYYYMMDD-Dataset_name
* e.g. 20230907-RNAseq_BK21dpi

Scripts  
* Pipeline_name_0N_<script_function/programme_command>.sh e.g. RNAseq_DE_04_kallisto_index.sh / RNAseq_28a_generate_log2fc_qval_table_donor-matched.R
* Number the script to denote at what stage in the workflow it is used (if applicable).
* Use letters a, b, c etc. for slightly different versions of the same script e.g. RNAseq_28a_generate_log2fc_qval_table_donor-matched.R and RNAseq_28b_generate_log2fc_qval_table_unmatched.R

### Create new project directory

Name using naming system
Symlinks to raw files

### Run the workflow

Use symlinks  
Finding reference files (most genome indicies already exist)  
Custom bash scripting (template available), name using naming system  

### Using git [OPTIONAL]

For version control, backup, data/code sharing, and syncing projects across Viking2 and a personal workstation.  
.gitignore (template available)  

### Publish completed project on GitHub

* This is easier if you have initiated git in your project directory and you already have a remote repository. 
* Write a README.md file to accompany your project and add to your project directory. Here is a GitHub README.md template. 
* Make final commit and push changes to GitHub. 

## Best practices

* Keep a **lab book** to document all of your work. Include code snippets, plots, and exact versions of any software used. Here is a lab book [template](https://docs.google.com/document/d/1ySzxTRnMpt9aG01iwE2VfKpvgigy6ELyRxGaz3vkoEo/).  
* Stick to the **file/directory naming system** for project directories and scripts. For other files/subdirectories inside your project directory, use your own naming system and keep it as consistent as possible.  
* Store intermediate files in **chronologically numbered directories**, e.g. 00_raw-links/, 01_quality-control/, 02_fastq-trimmed/, 03_bam/, 99_logs etc.  
* Keep **log files** from batch submissions to refer back to if needed.  
