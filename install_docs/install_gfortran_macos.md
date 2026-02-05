## installing SWASH using gfortran on macOS

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
