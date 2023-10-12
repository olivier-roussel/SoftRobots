# Installing SOFA and SoftRobots plugins with conda

This tutorial describes how to install a release of SOFA and the required plugins in order to run the Tripod tutorial.

## <i>Note</i>
> SOFA conda packages are not available yet on official channels such as conda-forge (the work is in progress), but as we will see, a preliminary version of these packages are available on a dedicated channel.

If you are already familiar to conda and your conda installation is configured with `conda-forge` as the default channel, then you can skip the first sections and directly go to the [SOFA conda packages installation section](#install_sofa_conda_package). Otherwise, these steps will guide you on how to install and configure conda first. 

Conda is both a package and environment manager. It provides a simple way to install packages inside an isolated environment, avoiding the 
installation alongside system wide packages and letting you switch between different environment that may use different and/or 
incompatible versions. More especially, it can easily handle different Python versions and installations.
conda packages are not restricted to Python and can be written in any language, so it is well suited for C++ or C++ / Python packages.
It also provides an mecanism to handle package dependency and can detect dependencies incompatibilities, preventing the user 
to break its environment. 
 
If you are new to conda, this <a href=https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf> cheat sheet</a> 
might be also very useful.

# Installing conda

We recommend to install conda from the installers provided by the conda-forge community, such as 
<a href=https://github.com/conda-forge/miniforge#mambaforge>Mambaforge</a>, which already includes 
<a href=https://github.com/mamba-org/mamba>Mamba</a> tools.

The use of Mamba is highly recommended, as it provides a much more faster way to install conda packages, thanks to more efficient dependency solver.
To use Mamba instead of conda, just replace `conda` by `mamba` in your command line invocation, e.g. replace:
```
conda install my-package
```
by:
```
mamba install my-package
```

## <i>Note</i>

> It is also possible to configure conda to use the mamba dependency solver by default. For more information, please check <a href=https://www.anaconda.com/blog/a-faster-conda-for-a-growing-community>this Anaconda's blog post</a> or the official <a href=https://github.com/conda/conda-libmamba-solver>libmamba solver GitHub page</a>.


# Checking your (existing or fresh) conda installation

The initial conda configuration can differ depending on the installer and distribution you have used. If you
installed conda using Miniforge or Mambaforge distributions as in previous section, then you shall be fine and you can skip this section and directly go to the [SOFA conda packages installation section](#install_sofa_conda_package). If you have an old conda installation, used another installer or are
unsure about your conda configuration, please proceed this section carefully.
First, you need to ensure that the conda-forge channel is enabled in your conda installation
and has priority:
```
$ conda config --show channels
```

Check that conda-forge is present in the list and appears first:
```
channels:
  - conda-forge
  - defaults
```

## <i>Note</i>

> Alternatively, you may have removed the `defaults` channel to prevent any incorrect mixing with the `conda-forge` channel. In this case, you could have only the `conda-forge` present in the list
and you can skip the configuration of the `channel_priority` that will follow.

If not present in the list, you to add it permanently to your channels list using:
```
$ conda config --add channels conda-forge
```

If the order in the list (channel priority) is reversed, just type re-add 
the conda-forge channel using the previous command and you should get the desired output.

We also strongly advise that you use the strict channel priority mode, as recommended by conda 
 <a href=https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html#strict>here</a>:
```
$ conda config --show channel_priority    
```

## <i>Note</i>

> You can also access to your conda configuration by editing the `~/.condarc` file.

# [Install SOFA conda packages](#install_sofa_conda_package)

Once everything is set up, you can install the conda packages of the last SOFA and its plugins release (v23.06).

## <i>Note</i>

> These conda packages are a prerelease and supported platforms are limited to Linux and Windows. Support for macOS is not operational yet.

## Setup a dedicated conda environment

Create a new conda environment for the tutorial:

```
conda create -n jnrr-tripod-tutorial
```

Activate the newly created environment:

```
conda activate jnrr-tripod-tutorial
```

## Install conda packages

Install SOFA and required plugins in this conda environment with `conda` or with `mamba` (faster):
```
$ conda install sofa sofa-softrobotsinverse -c olivier.roussel
```
or 
```
$ mamba install sofa sofa-softrobotsinverse -c olivier.roussel
```

This will automatically install other required SOFA plugins such as `sofa-softrobots`, `sofa-python3`, `sofa-stlib`, as well as all required dependencies.
