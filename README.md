# DeepMD-kit- Colin's tutorial so far

# Table of Contents
- [About](#About)
  * [How DeePMD- kit works](#How DeePMD- kit works)
    + [Sub-sub-heading](#sub-sub-heading)
  * [License and Credits](#License and Credits)
- [Installation](#Installation)
  * [Download using Conda](#Download using Docker or Conda)
    + [Conda or Miniconda](#Miniconda)
  * [
- [Running Simulations](#heading-2)
  * [1](#sub-heading-2)
    + [Sub-sub-heading](#sub-sub-heading-2)
  * [2]
    + [Sub-sub-heading](#sub-sub-heading-3)
  
# About
<!-- toc -->

## How DeePMD- kit works

Here is where I will give a more comprehensive report on DeepMD-kit and specifically its potential usefulness to the lab- or researchers in general

## License and Credits
None of this kit and its code is mine, and you use this code you can use the citation below. The project DeePMD-kit is licensed under GNU LGPLv3.0.

Han Wang, Linfeng Zhang, Jiequn Han, and Weinan E. "DeePMD-kit: A deep learning package for many-body potential energy representation and molecular dynamics." Computer Physics Communications 228 (2018): 178-184.


# Installation

If some video tutorials are necessary to guide someone through the installation and use of DeePMD- kit I could put some here:

[Youtube Link](https://www.youtube.com/watch?v=E-Yi_3pVUow&t=1s)

# Create instance of Linux to use DeePMD-kit 

DeePMD- kit is native to Linux, so you are required to run it there. If you already have an instance of Linux, skip this step. If you need to install Linux, I will provide a quick tutorial on what I found to be the best way to install and run Linux on a PC.

## Download using Conda

To install the DeePMD-kit, you must first install Anaconda or Miniconda. If storage space on your instance of Linux is an issue, use Miniconda. If you already have one of these, skip the next step. 

Install Anaconda here or Miniconda here. 

From here on I will only focus on the CPU version of this kit. If I find out that the GPU version may also be necessary, then I will include it. 

Open the terminal in Linux, and begin the installation. 
To install the CPU version via Conda: 

`conda install deepmd-kit=*=*cpu lammps-dp=*=*cpu -c deepmodeling`

## Install python interface with TensorFlow

First, check and ensure that you have python and the compiler on your machine:

`python3 --version`

`gcc --version`

`pip3 --version`

`virtualenv -- version`

If not, install them using directions tbd. 

It is recommended to create a virtual environment in order to isolate package installation from the system. In doing so, in the future when doing work with DeePMD-kit or TensorFlow, it will be necessary to activate the virtual environment. 

create a new virtual environment:

`virtualenv --system-site-packages -p python3 ./venv`

Here is how you activate the virtual environment, and this is the command you will use anytime you want to activate the virtual environment:

`source ./venv/bin/activate`

When the virtual environment is active, your shell prompt is prefixed with `(venv)`

Whenever you are done using DeePMD-kit or TensorFlow, make sure to exit the virtual environment later by `deactivate`. 

Upgrade pip if necessary:
`pip install --upgrade pip`

Now, go forward with installing TensorFlow:

`pip install --upgrade tensorflow`

Verify the install:

`python -c "import tensorflow as tf;print(tf.reduce_sum(tf.random.normal([1000, 1000])))"`

To verify the installation, run:

`python -c "import tensorflow as tf; sess=tf.Session(); print(sess.run(tf.reduce_sum(tf.random_normal([1000, 1000]))))"`

TensorFlow should now be installed.

## Install DeePMD-kit's python interface

First, clone the DeePMD-kit source code

`cd /some/workspace`

`git clone --recursive https://github.com/deepmodeling/deepmd-kit.git deepmd-kit -b devel`

You can record the location of the source with `deepmd_source_dir`

`cd deepmd-kit`
`deepmd_source_dir = pwd` 

Then execute

`pip install`

To test the installation, you may execute

`dp -h`

## Install the C++ Interface IMPORTANT

`cd deepmd-kit/source
mkdir build
cd build`

To install DeePMD-kit into path `$deepmd_root` then execute cmake

`cmake -DTENSORFLOW_ROOT=$tensorflow_root -DCMAKE_INSTALL_PREFIX=$deepmd_root ..`

The GPU and CUDA tool-kit may be necessary here...

`cmake -DUSE_CUDA_TOOLKIT=true -DTENSORFLOW_ROOT=$tensorflow_root -DCMAKE_INSTALL_PREFIX=$deepmd_root ..`

If the cmake has executed successfully, then run 

`make
make install`

If it works fine, then there should be the following executables and libraries installed in `$deepmd_root/bin` and `$deepmd_root/lib`

`$ ls $deepmd_root/bin
dp_ipi
$ ls $deepmd_root/lib
libdeepmd_ipi.so  libdeepmd_op.so  libdeepmd.so`



## Install LAMMPS DeePMD-kit module ALSO IMPORTANT

The deepmd-kit also provides a module for running MD simulations with LAMMPS. You can make the DeePMD-kit module for LAMMPS

`cd $deepmd-kit/source/build
make lammps`

### How to retrieve LAMMPS and install it 

Uncompress the LAMMPS file `lammps-stable.tar.gz`. Here is where I will explain where and how to find LAMMPS, and how to install it so that it can be used with DeePMD-kit. 

`cd /some/workspace
tar xf lammps-stable.tar.gz`

`cd lammps-31Mar17/src/
cp -r $deepmd_source_dir/source/build/USER-DEEPMD .`

`make yes-user-deepmd
make mpi -j4`

This should end up with an executable `lmp_mpi` FIND MPI!


# Use the DeePMD-kit

## Running an example simulation?

### Prepare Model

### Train Model

### Freeze Model

### Use model to run simulation with native MD code

### Use model with LAMMPS to run simulation

# Colin's next plans for the tutorial?


- Try to make my own example for MD simulations with deepmd kit

- Give detailed walkthrough for incorporating LAMMPS with DeePMD-kit 









