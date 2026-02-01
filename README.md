# SWASH
[![License: GPL v3](https://img.shields.io/badge/License-GPL_v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

SWASH is a general-purpose numerical tool for simulating unsteady, non-hydrostatic, free-surface, rotational flow and transport phenomena in coastal waters as driven by waves, tides, buoyancy and wind forces.
It provides a general framework for describing wave transformations from deep water to a beach, port or harbour, complex changes to rapidly varied flows, and density driven flows in coastal seas, estuaries, lakes and rivers.

## documentation

- [website](https://swash.sourceforge.io)
- [user manual](https://swash.sourceforge.io/online_doc/swashuse/swashuse.html)
- [scientific documentation](https://swash.sourceforge.io/online_doc/swashtech/swashtech.html)
- [repository](https://gitlab.tudelft.nl/citg/wavemodels/swash)

## installing SWASH

The SWASH source code is written in Fortran90 and is available at the [Gitlab repository](https://gitlab.tudelft.nl/citg/wavemodels/swash).
You can either install the pre-compiled SWASH package directly on your computer or install using a Fortran90 compiler.

### installation methods

#### 1. pre-compiled packages

A pre-compiled binary distribution allows quick installation without requiring compilation.
The SWASH 11.01 binaries are available for the following OS:

- [Windows 11](https://swash.sourceforge.io/download/zip/SWASH-11.01-Windows.exe)
- [Linux](https://swash.sourceforge.io/download/zip/SWASH-11.01-Linux.tar.gz)
- [macOS Intel](https://swash.sourceforge.io/download/zip/SWASH-11.01-macOS.tar.gz)
- [macOS Silicon](https://swash.sourceforge.io/download/zip/SWASH-11.01-macOS-Silicon.tar.gz)

Note that the tarbar files can be extracted in any folder and has no further installation steps.
Do not forget to add the installed folder to your path.

#### 2. installation from source

    - [installing SWASH using gfortran on Windows 11](install_gfortran_win11.md)
