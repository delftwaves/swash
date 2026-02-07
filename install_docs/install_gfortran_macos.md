## installing SWASH using gfortran on macOS

### table of contents

- [prerequisites](#prerequisites)
- [installation SWASH](#installation-swash)
- [options for configuring SWASH](#options-for-configuring-swash)
- [building with MPI support](#building-with-mpi-support)
- [clean up](#clean-up)

### prerequisites

The following packages must be installed first:

- gfortran
- cmake
- ninja
- perl

These packages can be installed using system package managers such as Homebrew, MacPorts and Fink.
Here, we will use [Homebrew](https://brew.sh). You may install Homebrew first (visit its homepage, copy the installation command, open a terminal and paste it into your terminal, and press Enter)
or update it: `brew update`.

With the command `brew list` you can check the installed packages (or _formulae_) on your macOS. If desired, upgrade these packages first by typing `brew upgrade`.
Below are the instructions for installing the required packages.

First, install GCC (Gnu Compiler Collection) that includes `gfortran` by opening a terminal (Applications > Utilities and search for the Terminal app) and typing the following command

```bash
brew install gcc
```

To verify the installation, type `which gfortran` in the terminal. It should return a path where `gfortran` has been installed.
On Apple Silicon, the compiler will be installed into the folder `/opt/homebrew/bin/`, while on an older Intel Mac, it will be
installed in `/usr/local/bin`.

Alternatively, type `gfortran --version` in the terminal. It should return a version number.

Next, open a terminal and run the following command

```bash
brew install cmake
```

and then

```
brew install ninja
```

These commands will installed `CMake` and `ninja` on your machine.

Usually, `perl` is pre-installed on macOS. This can be checked with the command `perl -v`. Otherwise, you may install it by running the command `brew install perl`.

#### Verify installations

Verify the required installations by checking their versions, as follows

```bash
gfortran --version
```

```bash
cmake --version
```

```bash
ninja --version
```

```bash
perl --version
```

If no error is reported, then the installation was successful.

Note: the `CMake` version must be at least 3.20 or newer and the `perl` version is 5 or higher.

### installation SWASH

Once the prerequisites are taken care of, installing SWASH on your machine is a four-step process.

#### 1.  download SWASH

Open a Terminal app, copy the command below to paste into the terminal, and press Enter.

```bash
git clone https://gitlab.tudelft.nl/citg/wavemodels/swash.git
```

#### 2. configure SWASH

```bash
make config
```

#### 3. build SWASH

```bash
make
```

#### 4. install SWASH

```bash
make install
```
SWASH is installed at folder `$HOME/wavemodels/swash` by default. To run SWASH, you need to make sure that this directory is added to your system's `PATH`.
Open the terminal and enter

```bash
export PATH=$PATH:$HOME/wavemodels/swash
```

You can check the new value of `PATH` by echoing it: `echo $PATH`. However, to set this permanently, you need to add it to your `~/.bash_profile` or `~/.bashrc` file.

### options for configuring SWASH

If desired, the build can be configured by passing one or more options below to `make config`.

    fc=<compiler>   - the Fortran90 compiler to use [default is determined by CMake]
    mpi=on          - enable build of SWASH with MPI [off by default]
    prefix=<folder> - set the installation folder [$HOME/wavemodels/swash by default]

For example, the following command

```bash
make config fc=gfortran prefix=/usr/local/swash
```

will configure SWASH to be built using `gfortran` and then install it at `/usr/local/swash`.

### building with MPI support

The SWASH source code also supports memory-distributed parallelism for high performance computing applications.
A message passing approach is employed based on the Message Passing Interface (MPI) standard that enables communication between independent processors.

Popular implementations are [Open MPI](https://www.open-mpi.org) and [MPICH](https://www.mpich.org).
The first one is typically offered by the package managers of Linux and macOS and can be combined with GCC such as gfortran.
The easiest way to install Open MPI is by using the Homebrew package manager.

Before installing Open MPI, make sure that your system is up to date and that GCC has been installed, see [prerequisites](#prerequisites).
To install Open MPI, run

```bash
brew install openmpi
```

To verify whether the installation was successful, run the following command

```bash
ompi_info --version
```

or

```bash
mpirun --version
```

Once Open MPI is operational, we proceed to build SWASH. First, we configure SWASH to be built with support for Open MPI, as follows

```bash
make config fc=mpifort mpi=on
```

The actual building is done by typing

```bash
make
```

Finally, to install SWASH, run the following command

```bash
make install
```

SWASH is now ready for high performance computing.

### clean up

To remove all files installed by `make install`, type the following command

```bash
make uninstall
```

If you want to remove the build directory and all files that have been created after running `make` or `make build`, then run

```bash
make clobber
```
