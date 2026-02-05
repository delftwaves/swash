## installing SWASH using gfortran on Linux

The most common Linux distributions are
- RHEL, CentOS Stream, Rocky Linux, Fedora (RPM-based Linux)
- Debian, Ubuntu, Mint (Debian-based Linux)

with which the installation instructions below can be applied.

### table of contents

- [prerequisites](#prerequisites)
- [installation SWASH](#installation-swash)
- [options for configuring SWASH](#options-for-configuring-swash)
- [clean up](#clean-up)

### prerequisites

The following packages must be installed first:

- gfortran
- cmake
- ninja
- perl

These packages can be installed using OS-specific package managers.

#### RPM-based Linux distributions

The default package manager is `dnf`. First, update the system

```bash
sudo dnf update
```

Next, run the following command to install GCC (Gnu Compiler Collection) on the system

```bash
sudo dnf install gcc
```

and then `gfortran`

```bash
sudo dnf install gcc-gfortran
```

To install `cmake`, enter

```bash
sudo dnf install cmake
```

Finally, install `ninja` by running the following command

```bash
dnf install ninja-build
```

Before installing `perl`, check if it is already present on your Linux distribution, by typing

```bash
perl -v
```

If `perl` is not installed, the shell reports that this command is not found.
In that case, install the perl interpreter as follows

```bash
sudo dnf install perl
```

#### Debian-based Linux distributions

The package manager is `apt-get`. Open a command line terminal and run the following commands:

```bash
sudo apt-get update
```

followed by

```bash
sudo apt-get install build-essential cmake ninja-build gfortran
```

Note that the `build-essential` package installs essential tools and libraries for compiling the source code, including `gcc` and `make`.

The Linux flavors Debian, Ubuntu and Mint have `perl` installed by default.

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

#### 1.  download SWASH

```bash
git clone https://gitlab.tudelft.nl/citg/wavemodels/swash.git
```

Paste this into a shell terminal.

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
make config mpi=on
```

will configure SWASH to be built that supports parallel computing using the MPI paradigm. Note that this only works if the MPI libraries are available on your machine.
This will be checked by `CMake` after typing the above command.

### clean up

To remove the build directory and all files that have been created after running `make` or `make build`, type the following command

```bash
make clobber
```

If you want to remove all files installed by `make install`, then run

```bash
make uninstall
```
