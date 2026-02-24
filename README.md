# SWASH

[![release](https://img.shields.io/badge/release%20-%20v11.01%20-%20brightgreen?color=success)]()
[![site](https://img.shields.io/badge/sourceforge%20-%20site%20-%20blue?logo=sourceforge&color=informational)](https://swash.sourceforge.io)
[![repo](https://img.shields.io/badge/gitlab%20-%20repo%20-%20blue?logo=gitlab&color=informational)](https://gitlab.tudelft.nl/citg/wavemodels/swash)
[![image](https://img.shields.io/badge/delftwaves%2Fswash%20-%20image%20-%20blue?logo=docker&color=informational)](https://hub.docker.com/r/delftwaves/swash)
[![doi](https://img.shields.io/badge/DOI%20-%2010.1016%2Fj.coastaleng.2011.05.015%20-%20red?color=informational)](https://doi.org/10.1016/j.coastaleng.2011.05.015)
[![license](https://img.shields.io/badge/license%20-%20GPL_v3%20-%20yellow?color=important)](/LICENSE)

SWASH is a general-purpose numerical tool for simulating unsteady, non-hydrostatic, free-surface, rotational flow and transport phenomena in coastal waters as driven by waves, tides, buoyancy and wind forces.
It provides a general framework for describing wave transformations from deep water to a beach, port or harbour, complex changes to rapidly varied flows, and density driven flows in coastal seas, estuaries, lakes and rivers.

### table of contents

- [installation](#installation)
  - [installation methods](#installation-methods)
    - [docker container](#docker-container)
    - [pre-compiled binary packages](#pre-compiled-binary-packages)
    - [installation from source](#installation-from-source)
- [run instructions](#run-instructions)
  - [usage of built SWASH](#usage-of-built-swash)
    - [local copy of SWASH](#local-copy-of-swash)
    - [from Docker image](#from-docker-image)
    - [use with Apptainer or Singularity](#use-with-apptainer-or-singularity)
- [documentation](#documentation)

## installation

The SWASH source code is written in Fortran90 and is available at the [Gitlab repository](https://gitlab.tudelft.nl/citg/wavemodels/swash).
You can either install the pre-compiled SWASH package directly on your computer or configure, build and install SWASH using a Fortran90 compiler.
Alternatively, you can run SWASH immediately using a docker container. Especially users new to SWASH might find this very helpful.

### installation methods

1. [docker container](#docker-container)
2. [pre-compiled binary packages](#pre-compiled-binary-packages)
3. [installation from source](#installation-from-source)

#### docker container

A docker container bundles an application (here SWASH) with all its dependencies, including libraries, configuration files, and a lightweight OS kernel (usually Linux Ubuntu)
into a single package, and can be used to run the application directly on any OS platform. To run the container, one needs to install the [Docker Engine](https://docs.docker.com/engine/install/)
in their machine. This engine is available for Windows, Linux, and macOS via [Docker Desktop](https://www.docker.com/products/docker-desktop/).

After installing Docker Desktop, you can test SWASH and check if it runs properly.
Open a terminal, copy and paste the following command into the terminal and press Enter:

```bash
docker run delftwaves/swash
```

This `docker run` command first pulls the image `delftwaves/swash` from the [Docker Hub](https://hub.docker.com), which might take a few moments.
Next, it creates a new container based on this image and then the SWASH executable within this container will be run.
If the installation was successful, you should see a message saying that SWASH ran successfully.

To run your own SWASH application, download the official [SWASH docker image](https://hub.docker.com/r/delftwaves/swash) from the Docker Hub repository.
Like the SWASH source code, this image is distributed under [GNU GPL v3 license](https://gitlab.tudelft.nl/citg/wavemodels/swash/-/blob/main/LICENSE).

#### pre-compiled binary packages

A pre-compiled binary distribution allows quick installation without requiring compilation.
The SWASH 11.01 binaries are available for the following OS/ARCH:

- [Windows 11 (AMD64)](https://swash.sourceforge.io/download/zip/SWASH-11.01-Windows.exe)
- [Linux Ubuntu 24.04 LTS (AMD64)](https://swash.sourceforge.io/download/zip/SWASH-11.01-Linux.tar.gz)
- [macOS Monterey 12.7.6 (AMD64)](https://swash.sourceforge.io/download/zip/SWASH-11.01-macOS.tar.gz)
- [macOS Sequoia 15.7.3 (ARM64)](https://swash.sourceforge.io/download/zip/SWASH-11.01-macOS-Silicon.tar.gz)

Important notes:
- These binaries are 64-bit only and, additionally, cannot be executed on multiple cores or threads.
- Be aware that you may run into compatibility issues when another OS version (e.g., Windows 7, 32-bit Windows 10) or
  distro (e.g., Linux Mint, Rocky Linux) is installed on your machine, or another CPU architecture (e.g., i386/i686, x86_64, AMD64, ARMv7, ARM64).
  If this is the case, then [Docker](#docker-container) might be a good alternative for you.
- The tarbar files can be extracted in any folder (`tar xzf SWASH-11.01-<OS>.tar.gz` with `OS = Linux` or `macOS`) and has no further installation steps.
  However, do not forget to add the installed folder to your path. Open a command line terminal and enter:

  ```bash
  export PATH=$PATH:/your/SWASH/folder/
  ```

  Add this line to your `~/.bash_profile` or `~/.bashrc` file to automatically set this new `PATH` every time you log in.
- The macOS executables require the GCC (GNU Compiler Collection) package. Open a terminal (Applications > Utilities and search for the Terminal app),
  copy and paste the following command, and hit Enter:

  ```bash
  brew install gcc
  ```

#### installation from source

- [installing SWASH using gfortran on Windows 11](install_docs/install_gfortran_win11.md)
- [installing SWASH using gfortran on Linux](install_docs/install_gfortran_linux.md)
- [installing SWASH using gfortran on macOS](install_docs/install_gfortran_macos.md)

## run instructions

SWASH can be run on various architectures, including laptops, HPC machines and cloud-based clusters,
Depending on your choice of [installed SWASH](#installation-methods), you can run the simulations locally on an OS platform (Windows, Linux or Mac)
via your own built SWASH or via Docker. Additionally, you can run SWASH on HPC with the SWASH docker image using Apptainer or Singularity.

### usage of built SWASH

1. [local copy of SWASH](#local-copy-of-swash)
2. [from Docker image](#from-docker-image)
3. [use with Apptainer or Singularity](#use-with-apptainer-or-singularity)

#### local copy of SWASH

The provided run scripts (`swashrun` and `swashrun.bat`) enable the user to properly and easily run SWASH both serial as well as parallel.

For Windows users, open a terminal (hit the Window key + R, type `cmd` and click OK), navigate to the folder containing your SWASH input files
(command file, grid, bathymetry, etc.), copy and paste the following command, then replace `<SWASH-command-file-without-extension>`
by the name of your SWASH command file without extension (assuming it is `sws`), and hit Enter:

```bat
swashrun <SWASH-command-file-without-extension>
```

while for Linux and Mac users, type in an opened terminal the following command:

```bash
swashrun -input <SWASH-command-file-without-extension>
```

Note that the script `swashrun` need to be made executable first, as follows:

```bash
chmod +rx swashrun
```

To redirect screen output to a file, use the sign `>`. Use an ampersand to run SWASH in the background. An example:

```bash
swashrun -input mytest > swashout &
```

For a parallel MPI run, you must specify the number of processors `<nprocs>` that will be launched, as follows:

```bat
swashrun <SWASH-command-file-without-extension> <nprocs>
```

in case of Windows, or

```bash
swashrun -input <SWASH-command-file-without-extension> -mpi <nprocs>
```

in case of Linux/Mac. By default, `nprocs = 1`.

#### from Docker image

The user can either choose between running SWASH directly using docker or the docker in interactive mode (option `-it`).

To run SWASH directly, copy and paste the following command, replace the required run parameters, and hit Enter:

```bash
docker run --rm -v .:/home/swash delftwaves/swash swashrun -input <SWASH-command-file-without-extension> -mpi <nprocs>
```

To run the SWASH container interactively, enter:

```bash
docker run -it --rm -v .:/home/swash delftwaves/swash bash
```

Once the interactive bash shell is started in the container, the user can access the commands available from Linux Ubuntu (e.g., `ls`, `find`, `which`) and SWASH (e.g., `swashrun`, `swash.exe`).

Notes:
- The option `-v .:/home/swash` ensures that the SWASH output files and the PRINT file created in the directory `/home/swash` of the docker container will store in your local current directory.
- The option `--rm` removes the exited container from your machine after terminating SWASH. (Check by invoking the command `docker ps -a`.)
- For a complete overview of the command `docker run`, please refer to this [page](https://docs.docker.com/reference/cli/docker/container/run/).

#### use with Apptainer or Singularity

The [SWASH docker image](https://hub.docker.com/r/delftwaves/swash) can be used with [Apptainer](https://apptainer.org) and [Singularity](https://sylabs.io/singularity/).
These container platforms are especially useful for running SWASH on HPC clusters, either locally or in the cloud
(e.g., [Microsoft Azure](https://azure.microsoft.com/en-us) and [Amazon Web Services](https://aws.amazon.com/)).

First, pull the docker image in the following way:

```bash
apptainer pull docker://delftwaves/swash:latest
```

This pull creates a singularity image named `swash_latest.sif`, which can then be run with standard Apptainer commands. For example:

```bash
apptainer run --bind .:/home/swash swash_latest.sif swashrun -input <SWASH-command-file-without-extension> -mpi <nprocs> > swashout &
```

where `<SWASH-command-file-without-extension>` is the name of your command file without extension and `<nprocs>` indicates how many processors need to be launched for a parallel MPI run.

To interactively execute commands within the SWASH container, enter:

```bash
apptainer shell swash_latest.sif
```

Consult this [page](https://apptainer.org/docs/user/main/quick_start.html#overview-of-the-apptainer-interface) to explore the possibilities with Apptainer.
A final note is that Apptainer is compatible with Singularity, implying that you may use the command `singularity` instead of `apptainer`.

## documentation

- [website](https://swash.sourceforge.io)
- [repository](https://gitlab.tudelft.nl/citg/wavemodels/swash)
- [user manual](https://swash.sourceforge.io/online_doc/swashuse/swashuse.html)
- [scientific manual](https://swash.sourceforge.io/online_doc/swashtech/swashtech.html)
