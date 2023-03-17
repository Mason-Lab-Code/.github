# Mason-Lab-Code

## Introduction 

The Mason-Lab-Code GitHub organization is a tool for sharing code between Mason Lab members. Scripts are organised into workflows. Each workflow has its own repository. 

## Getting started 

### Git and GitHub

If you are unfamiliar with Git and GitHub, try watching these introductory videos: 
* [*How to use GitHub*](https://www.youtube.com/watch?v=PQsJR8ci3J0)
* [*Git, GitHub, and GitHub Desktop for beginners*](https://www.youtube.com/watch?v=8Dd7KRpKeaE)

### GitHub account

If you don't already have a GitHub account, create one. Click *Sign Up* in the top right corner. 

### Membership

Once you have a GitHub account, ask Richard or Andrew to add you as a member of the Mason-Lab-Code organization. This will give you access to all of our code repositories.  

### Personal access token

To create a personal access token, follow the instructions [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token). 
Select "Tokens (classic)", not "Fine-grained tokens". 
When selecting scopes/permissions, tick "repo". 
Make a note of your personal access token. 
Every time Git prompts you for a "password" on the command line, enter your personal access token (not the password for your GitHub account). 

### Navigating

Have a look at the Mason-Lab-Code repositories. Each workflow has its own repository, containing all of the scripts required to run the workflow. Repositories also contain a README file, detailing the function of each script, all software requirements, links to any reference files needed, and instructions on how to implement the workflow. 

## Downloading a workflow 

Workflows can be downloaded directly to Viking or your personal workstation. Simply navigate to the directory in which you would like the scripts to reside, and clone the repository. 
```
# Example: downloading the NanoSeq repository
git clone https://github.com/Mason-Lab-Code/NanoSeq/
```

## Best practices 

Some tips for organising your work during your bioinformatics project: 
* Store the intermediate files for each step of your workflow in separate directories, numbered in chronological order - e.g. 04_fastqc_reports, 05_trimmed_fastq, 06_bam_files … 
* Name files consistently: donor-group_otherinformation.ext e.g. Y123-Diff_paired.fq.gz (so that the different pieces of information in the file name can be separated on the hyphen, underscore and dot). 
* Keep log files from batch submissions on Viking. 
* Keep an electronic lab book to document everything you do. Include code snippets, exact versions of software used, and figures. 
