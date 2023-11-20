# Mason Lab bioinformatics projects guide

## Introduction 

### Mason-Lab-Code GitHub organization

The Mason-Lab-Code GitHub organization is a centralised store for all of our code.  
  
Scripts are organised into workflows. Each workflow has its own repository.  
  
Repositories contain a README file, detailing the function of each script, all software requirements, links to any reference files needed, a workflow overview diagram, and instructions on how to implement the workflow. (GitHub account with Mason-Lab-Code membership required to view repositories.)  

### Viking group space (biol-cancerinf-2020) 

Path to Mason Lab group space on Viking: /mnt/scratch/project/biol-cancerinf-2020/  
  
This directory has centralised locations for our raw data, reference data, and code (synced with Mason-Lab-Code GitHub).  
  
biol-cancerinf-2020 directory structure:  
  
![image](https://github.com/Mason-Lab-Code/.github/assets/73953685/09b1cd94-b1ce-40f1-847e-d27f7b7b9542)

## Getting started 

### Viking account

If you haven't already, complete the [Viking user application form](https://docs.google.com/forms/d/e/1FAIpQLSfXkL10ypU6EQCBB2jS5oDwTpRMo77ppl7dvdbLnXm5zrKR7Q/viewform) to request a Viking account.  
Enter the Viking project code: **biol-cancerinf-2020**

### Using Viking

Viking is the University of York's high-performance computing (HPC) cluster. It has enough storage, memory and computing resources to carry out our bioinformatics projects. The [Viking documentation](https://vikingdocs.york.ac.uk/index.html) explains how to access and use Viking.  
  
Viking uses the Unix/Linux operating system. If you haven't used Linux before, you can read the [Linux shell](https://vikingdocs.york.ac.uk/beginners_guide/linux_shell.html) section of the Viking documentation.  
  
Make sure you are comfortable using basic Linux commands, logging in to Viking, submitting batch jobs, and running interactive sessions.  

### Git and GitHub

If you are unfamiliar with Git and GitHub, try watching these introductory videos: 
* [*How to use GitHub*](https://www.youtube.com/watch?v=PQsJR8ci3J0)
* [*Git, GitHub, and GitHub Desktop for beginners*](https://www.youtube.com/watch?v=8Dd7KRpKeaE)

You can try following this [Introduction to Git](https://github.com/alastair-droop/northernbug10-git-workshop) workshop, which outlines how to use git on the command line. 

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
* **YYYYMMDD-INITIALS-Project_name**
* e.g. 20231006-RG-ATACseq_Bladder_vs_Ureter
  
Raw data directories (inside biol-cancerinf-2020/Raw-Data/)  
* **YYYYMMDD-Dataset_name**
* e.g. 20230907-RNAseq_BK21dpi
  
Scripts  
* **Workflow_name_0N_<script_function/programme_command>.ext**
* e.g. RNAseq_DE_04_kallisto_index.sh / RNAseq_28a_generate_log2fc_qval_table_donor-matched.R
* Number the script to denote at what stage in the workflow it is used (if applicable).
* Use letters a, b, c etc. for slightly different versions of the same script e.g. RNAseq_28a_generate_log2fc_qval_table_donor-matched.R and RNAseq_28b_generate_log2fc_qval_table_unmatched.R

### Create new project directory

Create a new directory to complete your project. Name it using the naming system above (YYYYMMDD-INITIALS-Project_name).  

### git [OPTIONAL]

#### Why use git? 
* Synchronise your work across Viking and a personal workstation
* Keep your work under version control
* Backup your work to a remote repository
* Easily share code and results on GitHub

#### Initiate git
```
git init
```
#### .gitignore
The .gitignore file is important to specify the files and directories that you don't want git to track. This will include large files that we do not want to backup to GitHub.  
  
The gitignore template (path/) lists lots of common extensions for large files (/fq.gz / .fastq.gz / .bam etc.)  
  
Copy the contents of the gitignore template to the .gitignore file in your git-initiated directory.  

```
cp /mnt/scratch/projects/biol-cancerinf-2020/Mason-Lab-Code/gitignore.template /mnt/scratch/projects/biol-cancerinf-2020/Projects/<YYYYMMDD-INITIALS-Project_name>/.gitignore
```

Add any other expressions to match files and directories specific to your project that you don't want git to track.  

#### Complete your workflow and allow git to track changes
Write and run code, create new files and directories, move files around etc.  
  
Add contents of the directory to be tracked by git.  
```
git add . 
```
Check the status of the git tracking. 
```
git status
```
Commit changes
```
git commit -m "Commit message - what changes have been made?"
```
#### SSH key

Set up SSH Key (for authentication between Viking and GitHub)  
  
On Viking, print the content of your public key using the command below.  
```
cat ~/.ssh/id_alcescluster.pub
```
On GitHub, go to *Settings* > *SSH and GPG keys* > *New SSK key* and paste the content above into the *Key* box.  

#### Remote repository on GitHub

Create an empty remote repository on GitHub - go to the *Repositories* tab of your GitHub profile, and click *New*.  
  
Link your local repository with the new remote repository.  
```
git remote add origin git@github.com:<username>/new-remote-repo.git 
```
Push contents of local repository to GitHub. You will be prompted to enter your username and personal access token on the command line. 
```
git push -u origin master # or: git push -u origin main
```
Now, any further committed changes made to the local repository, can be pushed to the remote repository on GitHub. 
```
git push
```
And any committed changes made to the remote repository on GitHub, can be pulled to the local repository. 
```
git pull
```
#### Synchronise a project across Viking and personal workstations
* Now that this repository is linked to a remote repository on GitHub, you can synchronise your work across Viking and personal workstations by cloning the repository (git clone <repo URL>) and then pushing and pulling changes on the different systems.
* This might be useful if you are running computationally demanding steps of your workflow on Viking, and more personalised analyses on a local workstation, and you want to keep all of your work neatly in one directory. 

### Run the workflow

#### Symlinks

Create **symlinks** to raw files:  

```
mkdir /mnt/scratch/projects/biol-cancerinf-2020/Projects/<YYYYMMDD-INITIALS-Project_name>/00_raw/
ln -s /mnt/scratch/projects/biol-cancerinf-2020/Raw-Data/<YYYYMMDD-Dataset_name>/raw-file.fastq.gz /mnt/scratch/projects/biol-cancerinf-2020/Projects/<YYYYMMDD-INITIALS-Project_name>/00_raw/raw-file.fastq.gz
```

* Use **symlinks** to raw files as input, as opposed to the original raw files.
#### Reference files
* Any **reference files** required (e.g. reference genome FASTA) will be in /mnt/scratch/projects/biol-cancerinf-2020/Reference-Data/  
* The **genome index files** have already been created for some common aligners.
#### Custom bash scripts
* If writing any **custom bash scripts** for batch submissions on Viking, you can use the sbatch script template (/mnt/scratch/projects/biol-cancerinf-2020/Mason-Lab-Code/sbatch-script-template.sh). Remember to name the script according to the naming system above. If the script would be a useful addition to a workflow, we can add it to the appropriate Mason-Lab-Code repository. 

### Publish completed project on GitHub

* Write a README.md file to accompany your project and add to your project directory. Here is a GitHub README.md template. 
* Make final commit and push changes to GitHub. 

## Best practices

* Keep a **lab book** to document all of your work. Include code snippets, plots, and exact versions of any software used. Here is a lab book [template](https://docs.google.com/document/d/1ySzxTRnMpt9aG01iwE2VfKpvgigy6ELyRxGaz3vkoEo/).  
* Stick to the **file/directory naming system** for project directories and scripts. For other files/subdirectories inside your project directory, use your own naming system and keep it as consistent as possible.  
* Store intermediate files in **chronologically numbered directories**, e.g. 00_raw-links/, 01_quality-control/, 02_fastq-trimmed/, 03_bam/, 99_logs etc.  
* Keep **log files** from batch submissions.  
