# SWASH

SWASH is a general-purpose numerical tool for simulating unsteady, non-hydrostatic, free-surface, rotational flow and transport phenomena in coastal waters as driven by waves, tides, buoyancy and wind forces.
It provides a general framework for describing wave transformations from deep water to a beach, port or harbour, complex changes to rapidly varied flows, and density driven flows in coastal seas, estuaries, lakes and rivers.

## installing SWASH using gfortran on Windows 11

### prerequisites

The packages `gfortran`, `CMake`, `ninja` and `perl` must be installed first. They all included in [Strawberry Perl](https://strawberryperl.com) environment. After installing the latest version of Strawberry Perl, check whether the mentioned packages were successfully installed on your computer, by opening a command prompt and running the following commands

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
SWASH is installed at folder `%LocalAppData%\Programs\wavemodels\swash` by default. To run SWASH, you need to make sure that this directory is added to your system's `PATH`. Open command prompt and run

```bat
setx path "%path%;%LocalAppData%\Programs\wavemodels\swash"
```
