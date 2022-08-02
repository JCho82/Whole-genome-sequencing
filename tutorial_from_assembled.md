### 1. Set up a path for you to use conda (in terminal)
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

### 2. create a code environment for you (in terminal).
```
conda env create -f /dartfs-hpc/scratch/rnaseq1/environment.yml
```
Then activate your environment.
```
conda activate bioinfo
```

Now, you are all set to analyze your WGS data.

### 3. Combine your contigs (on a website).
The aligned samples have multiple contigs. To make a scaffold (a big and single genome), you should use one of scaffolding programs.

I am using CSAR (nucleic acids reseach, 2018, https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6030906/).

```
http://lu168.cs.nthu.edu.tw/CSAR-web/index.php
```
The files to input here will be provided.
For the target genome, you need to input each aligned sample.

For the reference genome, you should use a complete reference genone in FASTA format.
```
https://www.ncbi.nlm.nih.gov/genbank/
Type your stain name like JE2.
Find the complete genome (For instance, JE2, https://www.ncbi.nlm.nih.gov/nuccore/NZ_CP020619.1).
Save two files (Fasta file and genbank file).

```

Once done, you will have a file like (20220628_SN000_target.fna_scaffolding).
Since here, you need to use snapgene program (please install this program which is available in Dartmouth staffs and students).
In the zipped file, you can find "DNA files folder".

```
Open the biggest size of DNA files (the name would be Scaffold #1) with Snapgene.
```

```
Then, export the data in the FASTA format in the program (name it as sample1).
```

```
Check the file with Notepad (TextEdit in Mac).
```

You will find the file with starting with ">".
```
Please change the name after ">" to something like sample1 in the Notepad.
You should remember or jot down somewhere this name since you are going to use this name later.
It would be better to make it the same as your file name.
```

Repeat the same procedures with your samples.


Now, you will have seven samples (sample1.fa, sample2.fa, etc).


### 3. Copy your scaffold files into your own folder.
First, you need to make a folder to save your files.
```
mkdir scaffold_files
```

Second, tranfer your files to the folder, using FileZilla program.
```
Host: Discovery.dartmouth.edu
ID: your ID
password: your password
Port: 22

Drag or copy the files and paste to your new folder (scaffold_files).

```

### 4. Time to compare your genomes.

In terminal, check if you have Mummer program in your environment.

```
conda list
```

If you find it, then

Go to the folder where you moved your files.

```
ls -l

CD scaffold_files
```

To align your genomes, you need to make a delta file which is a kind of guiding file.

```
nucmer [option] <reference file> <query file>

nucmer --delta sample1.fa sample2.fa

```
(or your can put the real reference file like JE2 reference file) 

Then align your samples.

```
show-aligns <delta.file> <fasta ID for ref> <fasta ID for query>

show-aligns out.delta Sample1 Sample2
```

The fasta IDs are from the names after "<"


Now, you will see the aligned result from sample1 vs. sample2.
Since they are not annotated in the scaffold format, you are only able to see the loci where mutations occurred.

Thus, you need to manually compare the loci from JE2 ref (the genbank file).







