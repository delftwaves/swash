## installing SWASH using gfortran on Windows 11

### dependencies

The following packages must be installed first:

- gfortran
- cmake
- ninja
- perl

These packages are all included in [Strawberry Perl](https://strawberryperl.com) package.

After installing the latest version of Strawberry Perl, check whether the mentioned packages were successfully installed on your computer,
by opening a command prompt (press Windows key + R, type `cmd`, and hit Enter) and running the following commands

```bat
gfortran --version
```

```bat
cmake --version
```

Note: the `CMake` version should be at least 3.20 or higher.

```bat
ninja --version
```

```bat
perl --version
```

Note: the `perl` version should be at least 5.0.0 or higher.

### installation SWASH

#### 1.  download SWASH

```bat
git clone https://gitlab.tudelft.nl/citg/wavemodels/swash.git
```

#### 2. configure SWASH

```bat
make config
```

#### 3. build SWASH

```bat
make
```

#### 4. install SWASH

```bat
make install
```
SWASH is installed at folder `%LocalAppData%\Programs\wavemodels\swash` by default. To run SWASH, you need to make sure that this directory is added to your system's `PATH`.
Open command prompt ((press Windows key + R, type `cmd`, and hit Enter)) and type

```bat
setx path "%path%;%LocalAppData%\Programs\wavemodels\swash"
```
