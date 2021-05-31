# qiime2-2021.4-Pacbio-git

This file allows users to create a conda virtual evironment which has qiime2-2021.4 with the ability to process Pacbio long reads.

The codes processing long reads are from https://github.com/sixvable/q2-dada2-CCS.

#### Download .yml file
`git clone https://github.com/v0369012/qiime2-2021.4-Pacbio-git.git`

#### Create the environment
`cd ./qiime2-2021.4-Pacbio-git`

`conda env create -n qiime2-2021.4-Pacbio --file qiime2-2021.4-py38-linux-conda.yml`

#### Start the environment
`conda activate qiime2-2021.4-Pacbio`

### Add Pacbio processing codes
#### replace the original files
`cp ./q2-dada2-CCS/*.py /yourqiime2path/envs/qiime2-2021.4-Pacbio/lib/python3.8/site-packages/q2_dada2/`

`cp ./q2-dada2-CCS/run_dada_ccs.R /yourqiime2path/envs/qiime2-2021.4-Pacbio/bin`

#### Change the file format of run_dada_ccs.R
Because qiime2 is running on Linux, run_dada_css.R should be unix format.

`sudo apt-get install dos2unix # If you don't have 'dos2unix' commmand`

`dos2unix /yourqiime2path/envs/qiime2-2021.4-Pacbio/bin/run_dada_ccs.R`

#### Refresh qiime2
`qiime dev refresh-cache`

#### Check dada2 for Pacbio long reads
`qiime dada2 denoise-ccs --help`

#### Remove the downloaded folder
`rm -r ./q2-dada2-CCS`
