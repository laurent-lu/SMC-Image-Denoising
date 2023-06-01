# Spectral Monte Carlo Image Denoising
This is the code release attached to the paper [Spectral Monte Carlo Image Denoising](https://hal.univ-reims.fr/) submitted to SIGGRAPH ASIA 2023.

![shotCam](misc/teaser.png)

## Overview

This repository provides three BSDF plugins for the Mitsuba 0.6 renderer (https://github.com/mitsuba-renderer/mitsuba):

- **tm2**: Implements the 2-flux transfer model for opaque materials
- **tm2_dielectric**: Implements the 2-flux transfer model for transmissive materials
- **tm6**: Implements the 6-flux transfer model for opaque materials

**Notes**: Supplied code and data have been tested and validated on Windows 10 MSVC 2017 64-bits.

## Build instructions

### Prerequisities

- Visual Studio Community 2017 with "C++ Desktop Development" tools: https://docs.microsoft.com/en-us/cpp/build/vscpp-step-0-installation?view=msvc-150

- Python 2.7.18: https://www.python.org/downloads/. Please make sure to enable the **"Add python.exe to Path"** option during the installation process.

- Git command line client: https://git-scm.com/

### Cloning Mitsuba

For the sake of simplicity, we assume **C:/mitsuba/** as install directory, but the process remains valid for any other target location.

In a Git Bash prompt:

- $ cd /c/
- $ git clone https://github.com/mitsuba-renderer/mitsuba
- $ cd mitsuba
- $ git clone https://github.com/mitsuba-renderer/dependencies_win64 dependencies
- $ cp /c/mitsuba/dependencies/lib/*.dll /c/mitsuba/dependencies/bin/

### Cloning the code attached to the paper

In a Git Bash prompt:

- $ cd /c/
- $ git clone https://github.com/laurent-lu/TMbLM-Rendering.git

### Building the solution

- Copy all the files from **C:/TMbLM-Rendering/plugins/** to **C:/mitsuba/src/bsdfs/**

- Add the following lines to **C:/mitsuba/src/bsdfs/SConscript** just before the **Export('plugins')** directive in order to include the plugins files in the Mitsuba build:

```
plugins += env.SharedLibrary('tm2', ['tm2.cpp'])
plugins += env.SharedLibrary('tm2_dielectric', ['tm2_dielectric.cpp'])
plugins += env.SharedLibrary('tm6', ['tm6.cpp'])
```

- Open **C:/mitsuba/build/mitsuba-msvc2017.sln** with Visual Studio 2017
- Select **Release** as build configuration
- Build the solution (Menu **Build/Build solution**)
- Copy all the files from **C:/TMbLM-Rendering/data/** to **C:/mitsuba/dist/data/**

### Running the code

- Uncompress a scene .zip file from **C:/TMbLM-Rendering/scenes/**
- Drag and drop the XML scene file to **C:/mitsuba/dist/mitsuba.exe** to start the rendering. The corresponding output PNG image is saved in the scene folder at the end of the process.

**Notes**: Running **C:/mitsuba/dist/mtsgui.exe** results in a crash due to missing platform-specific Qt DLLs. Please see https://github.com/mitsuba-renderer/mitsuba/issues/52 where this issue is discussed and a workaround is proposed if Mitsuba's GUI is wanted.

## Citation

If you use this code, please consider citing our work accordingly: 

```
@inproceedings{randrianandrasana:2021:tmblmr,
 author = {Randrianandrasana, Joël and Callet, Patrick and Lucas, Laurent},
 title = {{Transfer Matrix Based Layered Materials Rendering}},
 journal = {ACM Transactions on Graphics (Proceedings SIGGRAPH)},
 volume = {40},
 number = {4},
 month = {August},
 year = {2021},
 doi = {10.1145/3450626.3459859}
}
```

## Contact

Feel free to send an e-mail to `mathieu.noizet[at]univ-reims.fr` or `laurent.lucas[at]univ-reims.fr` if you have any question.
