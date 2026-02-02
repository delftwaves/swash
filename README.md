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
You can either install the pre-compiled SWASH package directly on your computer or configure, build and install SWASH using a Fortran90 compiler.

### installation methods

#### 1. pre-compiled binary packages

A pre-compiled binary distribution allows quick installation without requiring compilation.
The SWASH 11.01 binaries are available for the following OS platforms:

- [Windows 11](https://swash.sourceforge.io/download/zip/SWASH-11.01-Windows.exe)
- [Linux Ubuntu 24.04 LTS](https://swash.sourceforge.io/download/zip/SWASH-11.01-Linux.tar.gz)
- [macOS Intel (Monterey 12.7.6)](https://swash.sourceforge.io/download/zip/SWASH-11.01-macOS.tar.gz)
- [macOS Silicon (Sequoia 15.7.3)](https://swash.sourceforge.io/download/zip/SWASH-11.01-macOS-Silicon.tar.gz)

Important notes:
- These binaries are 64-bit only and, additionally, cannot be executed on multiple cores or threads.
- Be aware that you may run into compatibility issues when another OS version (e.g., Windows 7, 32-bit Windows 10) or distro (e.g., Linux Mint, Rocky Linux) is installed on your machine.
- Note that the tarbar files can be extracted in any folder (`tar xzf SWASH-11.01-<OS>.tar.gz` with `OS = Linux` or `OS = macOS`) and has no further installation steps.
  However, do not forget to add the installed folder to your path. Open a command line terminal and enter

  ```bash
  PATH = $PATH:/your/SWASH/folder/
  export PATH
  ```

#### 2. installation from source

- [installing SWASH using gfortran on Windows 11](install_gfortran_win11.md)
- [installing SWASH using gfortran on Linux](install_gfortran_linux.md)
