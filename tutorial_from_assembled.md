### 1. Set up a path for you to use conda
```
source /optnfs/common/miniconda3/etc/profile.d/conda.sh
```

In order not to run this command each time you start a new session on discovery, it would be better to set it in a path.

nano is an editor to modify a file.
```
nano .bashrc
```
In the editor, add the code for source in .bashrc file.

Then, you need to make folders to store your own conda environments

```
cd ~
mkdir -p .conda/pkgs/cache .conda/envs
```

### 2. create a code environment for you.
```
conda env create -f /dartfs-hpc/scratch/rnaseq1/environment.yml
```
Then activate your environment.
```
conda activate bioinfo
```

Now, you are all set to analyze your WGS data.

### 3. Combine your contigs.
The aligned samples have multiple contigs. To make a scaffold (a big and single genome), you should use one of scaffolding programs.

I am using CSAR (nucleic acids reseach, 2018, https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6030906/).

```
http://lu168.cs.nthu.edu.tw/CSAR-web/index.php
```
The files to input here will be provided.
For the target genome, you need to input each aligned sample.
For the reference genome, you should use a complete reference genone in fasta format.

Once done, you will have a file like (20220628_SN000_target.fna_scaffolding).
Since here, you need to use snapgene program (please install this program which is available in Dartmouth staffs and students).
In the zipped file, you can find "DNA files folder".

Open the biggest size of DNA files (the name would be Scaffold #1) with Snapgene.

Then, export the data in FASTA format in the program.








### 3. Copy your aligned files into your own folder.
First, you need to make a folder to save your files.
```
mkdir aligned_files
```

Second, tranfer your files to the folder, using 

