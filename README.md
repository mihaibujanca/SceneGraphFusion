# SceneGraphFusion
![teaser](img/teaser.png)
**Authors**: [Shun-Cheng Wu][sc], [Johanna Wald][jojo], [Keisuke Tateno][keisu], [Nassir Navab][nassir] and [Federico Tombari][fede]

[sc]:http://campar.in.tum.de/Main/ShunChengWu
[keisu]:http://campar.in.tum.de/Main/KeisukeTateno
[jojo]:http://campar.in.tum.de/Main/JohannaWald
[nassir]:http://campar.in.tum.de/Main/NassirNavabCv
[fede]:http://campar.in.tum.de/Main/FedericoTombari

This is the SceneGraphFusion c++ framework. For the network part of the code, check [here](https://github.com/ShunChengWu/3DSSG).

# Prerequisites
## git, cmake
```
apt update
apt install git
# cmake
sudo apt install python3-pip
pip3 install cmake
# create ssh key and associate to your account in order to clone this project.
# * Generate new ssh key [link](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
# * Adding a new ssh key to your account [link](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)
```
# OpenCV, Eigen
```
# Eigen3 3.3.90  
# OpenCV 4.0.0  
# This project will try to install them locally if they were not found.
```
# Optional dependencies
With GUI:
```
# OpenGL & Glfw3
apt install freeglut3-dev libglfw3-dev
# Assimp
apt install libassimp-dev
```
With graph prediction:
```
# Onnxruntime
# See https://github.com/microsoft/onnxruntime
```

#### BUILD
build the basic segmentation system 
```
git clone {this_repo}
cd SceneGraphFusion
mkdir build
cd build
cmake ..
make
```
build with GUI or graph prediction, pass these options in cmake:
```
cmake -DBUILD_GRAPHPRED=ON -DBUILD_GUI=ON ..
```

# Run
```
./exe_GraphSLAM --pth_in path/to/3RScan/squence/
# or with GUI
./exe_GraphSLAM_GUI --pth_in path/to/3RScan/squence/
# to see usage and options 
./exe_GraphSLAM --help
```

We provide data loader for 3RScan dataset and ScanNet. For 3RScan you will need to generate rendered depths and aligned poses. See [3RScan](https://github.com/WaldJohannaU/3RScan/tree/master/c%2B%2B)

Example usage:

```
# For 3RScan:
./exe_GraphSLAM --pth_in ./dataset/3RScan/data/3RScan/4acaebcc-6c10-2a2a-858b-29c7e4fb410d/sequence/
# For ScanNet
./exe_GraphSLAM --pth_in ./dataset/scannet/scans/scene0000_00/scene0000_00.sens
# RUn with graph prediction
./exe_GraphSLAM --pth_in ./path/to/data --pth_model /path/to/model
```


# License
[![License](https://img.shields.io/badge/License-BSD%202--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause)

### Paper
If you find the code useful please consider citing our [paper](https://arxiv.org/pdf/2103.14898.pdf):

```
@inproceedings{Wu2021,
    title = {{SceneGraphFusion: Incremental 3D Scene Graph Prediction from RGB-D Sequences}},
    author = {Shun-Cheng Wu and Johanna Wald and Keisuke Tateno and Nassir Navab and Federico Tombari},
    booktitle = {Proceedings IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    year = {2021}
}
```
