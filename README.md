# Analysis of methylation data with minfi and conumee

[![Binder](http://mybinder.org/badge_logo.svg)](http://mybinder.org/v2/gh/chavez-lab/methylation-analysis-tutorial/HEAD?filepath=methylation.ipynb)

## Dependencies
- [R](https://www.r-project.org/)
- [minfi](https://bioconductor.org/packages/devel/bioc/vignettes/minfi/inst/doc/minfi.html)
- [conumee](https://bioconductor.org/packages/devel/bioc/vignettes/conumee/inst/doc/conumee.html)
- [jupyter lab](https://jupyter.org/try-jupyter/lab/?path=notebooks%2FIntro.ipynb)

## Installation
1. Install dependencies 
2. Run methylation.ipynb

## GenePattern Notebook Walkthrough
GenePattern Notebook is a cloud bioinformatics resource developed and maintained by the Mesirov lab at UCSD. It is designed for use by computational experts and newbies alike, and provides compute resources, a standard Linux operating system (OS), the programming languages Python and R, and the interactive software development tool Jupyter notebook. All of the steps in this walkthrough should equally work with minimal modification on your local Linux, Windows, or Mac OS (although we haven't tested it).
- Navigate to [GenePattern Notebook](https://notebook.genepattern.org/) and create an account.
- Create a new project methylation-analysis-demo
### Install dependencies
Most analyses use existing software written and distributed by someone else, called *packages*. Those packages in turn will require other third-party packages to run, called `dependencies`, which will in turn require more dependencies, etc. This tutorial uses the `minfi` and `conumee` packages to analyze Illumina methylation array data, but the entire *dependency tree* is about 266 different software packages, each with specific versions. We will use the `conda` *package manager*, preinstalled into your GenePattern Notebook account, to install these.
- In the top right hand corner of the interface, click `New` > `Terminal`. This will open a bash command line interface (CLI), which you can use to download resources and install software.
- **Download the code.** Git is a software for maintaining and distributing other software. Run the command `git clone git@github.com:chavez-lab/methylation-analysis-tutorial.git` on the CLI to download the code for this tutorial.
- **Set up your environment.** A *virtual environment* (VE) is an isolated set of software tools for running a particular task. We will create a virtual environment for all of the software required for methylation analysis using `conda`.
- The softwares required for this tutorial are listed in the `_environment.yml` file of this repository. Run `conda env update _environment.yml` to create the VE and install all dependencies. **This will take awhile to run.**
- Run `conda init; source ~/.bashrc`; the reason this is necessary is beyond scope of this tutorial. Briefly, if you don't run this, then `conda` will tell you to run this before you can run the next command.
- Run `conda activate methylation-analysis-tutorial` to enter your new VE.
- Run `R -e 'IRkernel::installspec(name = "methylation", displayname = "methylation")'`. This will make your environment accessible within GenePattern Notebook.
* TODO: Dockerize this so that the environment comes pre-distributed.
### Download data
Bioinformatics frequently requires lots of data. This tutorial will use methylation array data of 1,256 medulloblastomas.
- Download the data at [download link](https://16515-my.sharepoint.com/:u:/g/personal/laurelia_sbpdiscovery_org/EQHc9jxw5WJIvsnr46S2V_oBUagMAKQrreUZQ7jEBsvh9g?e=BlC5eS)
- In the GenePattern interface, navigate to the methylation-analysis-tutorial directory and upload data.zip using the `Upload` button in the GenePattern interface. **This will also take a long time.** Yes, we're working on a better way to do this.
- In your Terminal tab, `cd methylation-analysis-tutorial` to navigate to the tutorial directory
- `unzip data.zip`.
- You don't need the .zip file anymore. Delete it with `rm data.zip`.
- You are now done with the Terminal and can close it.
* TODO: Host this somewhere with a public download link. Could also include it in the Docker container.

## Todo
- Deploy code, data and environment somewhere to the cloud (binder? SDSC accounts? genepattern 
notebook? posit cloud?)

## Lab notebook
2023 course materials: https://www.dropbox.com/scl/fo/ikec8fs2xovk0onljsyd2/h?dl=0

Things I have learned so far:
- To set up your virtual environment with jupyter lab, see 
https://www.zainrizvi.io/blog/jupyter-notebooks-best-practices-use-virtual-environments/
- Lots of bioconda packages will will only build on intel cpus. If you are using conda and 
apple silicon, see 
https://stackoverflow.com/questions/71515117/how-to-set-up-a-conda-osx-64-environment-on-arm-mac
- Using conda to install R packages (minfi and conumee + dependencies) seems to exceed the 
RAM limit for [mybinder.org](mybinder.org). See 
https://discourse.jupyter.org/t/how-can-i-prevent-an-out-of-memory-error-in-github-actions/17294

