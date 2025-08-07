Download instructions:

Clone this repo to a directory of your choice.
Download HLOC and KAIR submodules

`git submodule update --init --recursive`

Installation instructions:

1. If not yet installed, install a conda distribution for our enviroment. I recommend
the [conda-forge](https://conda-forge.org/download/) installer.
1a. If other conda distributions are used i'd still suggest setting conda-forge as a primary channel:
    `conda config --add channels conda-forge`
    `conda config --set channel_priority strict`
2. Create and activate a new environment, with python 3.10 and pip
    `conda create -n computer_vision python=3.10 pip`
    `conda activate computer_vision`
    You may use `mamba` instead of `conda` if you prefer.
3. If you have an Nvidia GPU, check your driver version; I'll use cuda version `11.8` in this example, but it should
be the same, for others, as long as you replace `11.8` with your version.
4. Install pytorch 2.1.2 for your CUDA version (we use 2.1.2 for compatibility reasons, although it may work with
   newer versions). Check [here](https://pytorch.org/get-started/previous-versions/) on how to install with ROCM/cpu:
    `conda install  pytorch==2.1.2 torchvision==0.16.2 torchaudio==2.1.2 pytorch-cuda=11.8 -c pytorch -c nvidia`
5. Install colmap 3.12 and pycolmap 3.12. If a version with your CUDA driver is available it will automatically
   download the GPU-enabled version.
    `conda install colmap=3.12 pycolmap=3.12`
6. Install the complete CUDA package of your version from the nvidia channel (skip if cpu only):
    `conda install nvidia/label/cuda-11.8.0::cuda`
7. Install the tiny-cuda-nn bindings (may skip if no nvidia or if some wrong happens, it is just a speedup), may
   take a while:
    `pip install --upgrade-strategy only-if-needed ninja 'git+https://github.com/NVlabs/tiny-cuda-nn/#subdirectory=bindings/torch'`
7. Install the requirements for KAIR:
    `cd KAIR`
    `pip install --upgrade-strategy only-if-needed -r requirement.txt`
    `cd ..`
8. Install Hierarquical-Localization for Superpoint/SuperGlue/LoFTR:
    `cd Hierarchical-Localization`
    `pip install --upgrade-strategy only-if-needed -e .`
    `cd ..`
9. Install Nerfstudio:
    `pip install --upgrade-strategy only-if-needed nerfstudio`
10. You MAY run into some issues regarding numpy versions; check by running `ns-train --help` and if some errors regarding
    numpy come up, reinstall numpy to version 1.26.4 (you may also need to reinstall opencv): `pip install numpy==1.26.4 opencv-python'
11. Install ipympl for interactive matplotlib
    `pip install ipympl`

Post-installation instructions:

1. Download pretrained models from KAIR:
    `python main_download_pretrained_models.py --models "others" --model_dir "model_zoo"`
    `python main_download_pretrained_models.py --models "DnCNN" --model_dir "model_zoo"`
    `python main_download_pretrained_models.py --models "SwinIR" --model_dir "model_zoo"`

