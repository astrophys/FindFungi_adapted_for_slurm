# FindFungi_adapted_for_slurm
FindFungi adapted from IBM's LSF to SLURM
=======

# FindFungi-v0.23.3
I made small changes to Paul Donovan's FindFungi Code
(https://github.com/GiantSpaceRobot/FindFungi/tree/master/FindFungi-v0.23.3)
to permit it to run on a SLURM cluster. The compute nodes on the cluster are
2 socket motherboards with 10 Haswell cores per socket (20 cores per node)
with 128GB of RAM. We are currently running CentOS 6.9 on our cluster with 
GPFS.

## Changes Made:

1. Replaced \t with 4 spaces
2. Added some diagnostics to permit identifying bottlenecks
3. Removed all instances of LSF's bsub
4. Used sbatch array job to offload the Kraken work onto separate nodes.

The majority of the work seemed to run fine on our compute nodes.
The Kraken step was the only part that needed off loaded to additional
compute nodes.

## Getting Started

See Paul Donovan's webpage for complete details : 
https://github.com/GiantSpaceRobot/FindFungi/tree/master/FindFungi-v0.23.3

### Installation and Prerequisites
I installed FindFungi using the following dependencies, which differ slightly
from the Paul's recommendations.


* gcc/4.9.2
* coreutils 8.27
* python 2.7.10 (installed via Anaconda, https://anaconda.com/download. Used pip to install argparse, biopython, ete3)
* skewer 0.2.2
* kraken 1.0 (Used previous installation from metawrap, https://github.com/bxlab/metaWRAP)
* ncbi blast 2.2.31+
* R-3.4.2 (packages: wordcloud)
* graphviz 2.26.0 (installed via yum)

## Contributors

* Paul Donovan, PhD (email: pauldonovandonegal@gmail.com)
* Gabriel Gonzalez, PhD (e-mail: gagonzalez@czc.hokudai.ac.jp)

## License
This project is licensed under the MIT License.
