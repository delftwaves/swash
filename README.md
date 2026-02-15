# SWASH

[![release](https://img.shields.io/badge/release%20-%20v11.01%20-%20brightgreen?color=brightgreen)]()
[![site](https://img.shields.io/badge/sourceforge%20-%20site%20-%20blue?logo=sourceforge&color=blue)](https://swash.sourceforge.io)
[![repo](https://img.shields.io/badge/gitlab%20-%20repo%20-%20blue?logo=gitlab&color=blue)](https://gitlab.tudelft.nl/citg/wavemodels/swash)
[![doi](https://img.shields.io/badge/DOI%20-%2010.1016%2Fj.coastaleng.2011.05.015%20-%20red?color=blue)](https://doi.org/10.1016/j.coastaleng.2011.05.015)
[![license](https://img.shields.io/badge/license%20-%20GPL_v3%20-%20yellow?color=yellow)](/LICENSE)

SWASH is a general-purpose numerical tool for simulating unsteady, non-hydrostatic, free-surface, rotational flow and transport phenomena in coastal waters as driven by waves, tides, buoyancy and wind forces.
It provides a general framework for describing wave transformations from deep water to a beach, port or harbour, complex changes to rapidly varied flows, and density driven flows in coastal seas, estuaries, lakes and rivers.

### table of contents

- [installation](#installation)
  - [installation methods](#installation-methods)
    - [docker container](#docker-container)
    - [pre-compiled binary packages](#pre-compiled-binary-packages)
    - [installation from source](#installation-from-source)
- [usage](#usage)
- [documentation](#documentation)

## installation

The SWASH source code is written in Fortran90 and is available at the [Gitlab repository](https://gitlab.tudelft.nl/citg/wavemodels/swash).
You can either install the pre-compiled SWASH package directly on your computer or configure, build and install SWASH using a Fortran90 compiler.
However, especially for new users, you can also run SWASH immediately using a docker container.

### installation methods

1. [docker container](#docker-container)
2. [pre-compiled binary packages](#pre-compiled-binary-packages)
3. [installation from source](#installation-from-source)

#### docker container

A docker container bundles an application (here SWASH) with all its dependencies, including libraries, configuration files, and a lightweight OS kernel (usually Linux Ubuntu)
into a single package, and can be used to run the application directly on any OS platform.
However, you do need the [Docker Engine](https://docs.docker.com/engine/install/) to run the container.
This engine is available for Windows, Linux, and macOS via [Docker Desktop](https://www.docker.com/products/docker-desktop/).

After installing Docker Desktop, you can test SWASH and check if it runs properly.
Open a terminal, copy and paste the following command into the terminal and press Enter:

```bash
docker run --name myfirstswash delftwaves/check_swash
```

This `docker run` command first pulls the image `delftwaves/check_swash` from the [Docker Hub](https://hub.docker.com), which might take a few moments.
Next, it creates a new container based on this image called `myfirstswash`, and then the SWASH executable within this container is run after which the output will be created.

If the installation was successful, you should see a message saying that SWASH ran successfully. Additionally, you can retrieve the SWASH output file from the running
container `myfirstswash`:

```bash
docker cp myfirstswash:/home/swash/a11stw01.tbl .
```

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
- Note that the tarbar files can be extracted in any folder (`tar xzf SWASH-11.01-<OS>.tar.gz` with `OS = Linux` or `macOS`) and has no further installation steps.
  However, do not forget to add the installed folder to your path. Open a command line terminal and enter

  ```bash
  export PATH=$PATH:/your/SWASH/folder/
  ```

  Note that to set this new `PATH` permanently for different sessions, you need to add it to your `~/.bash_profile` or `~/.bashrc` file.

#### installation from source

- [installing SWASH using gfortran on Windows 11](install_docs/install_gfortran_win11.md)
- [installing SWASH using gfortran on Linux](install_docs/install_gfortran_linux.md)
- [installing SWASH using gfortran on macOS](install_docs/install_gfortran_macos.md)

## usage

## documentation

- [website](https://swash.sourceforge.io)
- [repository](https://gitlab.tudelft.nl/citg/wavemodels/swash)
- [user manual](https://swash.sourceforge.io/online_doc/swashuse/swashuse.html)
- [scientific manual](https://swash.sourceforge.io/online_doc/swashtech/swashtech.html)
