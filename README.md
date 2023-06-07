# Spectral Monte Carlo Image Denoising
This is the code release attached to the paper [Spectral Monte Carlo Image Denoising](https://hal.univ-reims.fr/) submitted to SIGGRAPH ASIA 2023.

![shotCam](misc/teaser.png)

## Overview

This repository provides our denoiser application  into the Mitsuba 3 renderer (https://github.com/mitsuba-renderer/mitsuba3):

**Notes**: Supplied code and data have been tested and validated on Linux (Ubuntu, debian, Manjaro) and Windows.

## Build instructions

### Prerequisities

- Visual Studio Code with Dev Container extension provided by Microsoft

- Docker 24.0.0 : https://www.docker.com/

- Git command line client: https://git-scm.com/

### Cloning Mitsuba

TODO ---> attendre la reorganisation du git

### Cloning the code attached to the paper

TODO ---> attendre la reorganisation du git

### Building the solution

#### With Docker
To compile Mitsuba with our plugin solution, you must use this command line (available directly in a jupyter notebook)

```
cd smc-image-denoising
mkdir build
cd build
cmake -GNinja

# Modify Mitsuba.conf file, line 86-88 to have :    
   "enabled": [
        "scalar_rgb", "scalar_spectral", "cuda_spectral"
    ],
    
ninja docstrings
ninja
source setpath.sh
```
#### Without Docker

follow this instructions : 

```
sudo apt update
sudo apt install -y clang libc++-dev libc++abi-dev cmake ninja-build libpng-dev libjpeg-dev libpython3-dev python3-distutils

pip install clang==14.0.0
pip install libclang==14.0.1
sudo apt-get install -y clang-format clang-tidy clang-tools clang clangd libc++-dev libc++1 libc++abi-dev libc++abi1 libclang-dev libclang1 liblldb-dev libllvm-ocaml-dev libomp-dev libomp5 lld lldb llvm-dev llvm-runtime llvm python3-clang 


pip install pybind11 pybind11_mkdoc
sudo apt install -y mkdocs
pip install mkdocs
```

### Running the code

To handle easly our code, we provide a jupyter notebook. In the container, start the jupyter notebook server with the following command line :

```
jupyter notebook --allow-root ./notebooks
```

Then, open the demo.ipynb.

In this notebooks, you have the different command line to build the repository, follow by different instruction to launch our denoiser in demo scene.

## Citation

If you use this code, please consider citing our work accordingly: 

```
@inproceedings{noizet:2023:smc-image-denoising,
 author = { Mathieu, Noizet and Robin, Rouphael and Stéphanie, Prévost and Hervé, Deleau and Luiz-Angelo, Steffenel and Lucas, Laurent},
 title = {{Spectral Monte Carlo Image Denoising}},
 journal = {ACM Transactions on Graphics (Proceedings SIGGRAPH)},
 volume = {XX},
 number = {X},
 month = {XXXX},
 year = {2023},
 doi = {}
}
```

## Contact

Feel free to send an e-mail to `mathieu.noizet[at]univ-reims.fr` or `laurent.lucas[at]univ-reims.fr` if you have any question.
