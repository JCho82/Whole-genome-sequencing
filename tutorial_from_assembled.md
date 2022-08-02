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
conda activate JC82env
```


