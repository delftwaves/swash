## installing SWASH using gfortran on Windows 11

### prerequisites

The following packages must be installed first:

- gfortran
- gmake
- cmake
- ninja
- perl

These packages are all included in [Strawberry Perl](https://strawberryperl.com) package.

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

To run SWASH, you need to make sure that this directory is added to your system's `PATH`.
Open command prompt (press Windows key + R, type `cmd`, and hit Enter) and type

```bat
setx path "%path%;%LocalAppData%\Programs\wavemodels\swash"
```

Note to check the new value of `%path%` by echoing, first close the command prompt terminal and then open again.
