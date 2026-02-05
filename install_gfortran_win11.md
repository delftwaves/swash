## installing SWASH using gfortran on Windows 11

- [prerequisites](#prerequisites)
- [installation SWASH](#installation-swash)
- [options for configuring SWASH](#options-for-configuring-swash)
- [clean up](#clean-up)

### prerequisites

The following packages must be installed first:

- gfortran
- gmake
- cmake
- ninja
- perl

These packages are all included in the [Strawberry Perl](https://strawberryperl.com) package.

After installing the latest release of Strawberry Perl, check whether the required packages were successfully installed on your computer,
by opening a command prompt (press Windows key + R, type `cmd`, and hit Enter) and running the following commands

```bat
gfortran --version
```

```bat
cmake --version
```

```bat
ninja --version
```

```bat
perl --version
```

If each of the above package reports a version number, then the installation was successful.

Note: the version number of `CMake` must be at least 3.20 or higher and the `perl` version is 5 or higher.

### installation SWASH

#### 1.  download SWASH

Open a command prompt, copy the command below, right-click in the prompt window to paste and press Enter.

```bat
git clone https://gitlab.tudelft.nl/citg/wavemodels/swash.git
```

#### 2. configure SWASH

```bat
gmake config
```

#### 3. build SWASH

```bat
gmake
```

#### 4. install SWASH

```bat
gmake install
```
SWASH is installed at folder `%LocalAppData%\Programs\wavemodels\swash` by default. The current value of `%LocalAppData%` can be checked by typing

```bat
echo %LocalAppData%
```

To run SWASH, you need to make sure that this directory is added to your system's `PATH`. Open command prompt and type

```bat
setx path "%path%;%LocalAppData%\Programs\wavemodels\swash"
```

Note to check the new value of `%path%` by echoing, first close the command prompt terminal and then open again.

### options for configuring SWASH

If desired, the build can be configured by passing one or more options below to `gmake config`.

    fc=<compiler>   - the Fortran90 compiler to use [default is determined by CMake]
    mpi=on          - enable build of SWASH with MPI [off by default]
    prefix=<folder> - set the installation folder [%LocalAppData%\Programs\wavemodels\swash by default]

For example, the following command

```bat
gmake config mpi=on
```

will configure SWASH to be built that supports parallel computing using the MPI paradigm. Note that this only works if the MPI libraries are available on your Windows machine.
(This will be checked by `CMake` after typing the above command.)
For installation of MPI on Windows 11, visit the website of [Microsoft MPI](https://www.microsoft.com/en-us/download/details.aspx?id=105289).

### clean up

To remove the build directory and all files that have been created after running `gmake` or `gmake build`, type the following command

```bat
gmake clobber
```

If you want to remove all files installed by `gmake install`, then run

```bat
gmake uninstall
```
