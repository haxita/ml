UE Deep Reinforcement Learning 2025S
Imitation Learning

This guide provides a step-by-step process for recreating the development
environment necessary for our project. These instructions are designed to 
ensure compatibility across various operating systems. Please follow them 
carefully to set up your environment.

CAUTION: If running the notebook in Colab, there already exists an updated
cell for installing the required dependencies. The following README is
important for students wanting to train the model locally.

1. Prerequisites

Before proceeding, make sure you have 'conda' and 'pip' installed on your
system. 

Conda: Follow the installation guide at Miniconda (https://docs.anaconda.com/free/miniconda/) 
or Anaconda (https://www.anaconda.com/download).
pip: Comes installed with Conda distributions, but to ensure it is updated run 'conda install pip'.
C++ Build Tools (Windows only): For the box2d-py (which require compilation), install the Microsoft Visual C++ Build Tools from
(https://visualstudio.microsoft.com/visual-cpp-build-tools/). 
During the installation, select “Desktop Development with C++” and ensure “MSVC v143 – VS 2022 C++ x64/x86 build tools” is checked.

If any questions arise at to how to set this up please write in the
Moodle forum and perhaps a setup tutorial can be organized.


2. Environment Setup

For convenience, pre-configured Conda environment files are provided for Windows and Ubuntu:

Windows: environment_windows.yml
Ubuntu: environment_ubuntu.yml

You can create the environment by running the following command:
conda env create -f environment_windows.yml  # For Windows
conda env create -f environment_ubuntu.yml   # For Ubuntu

Then, activate the environment:
conda activate drl-imit  # Windows
conda activate drl-imitation-learning  # Ubuntu


If you prefer to manually install dependencies, create a new environment:
conda create --name new_name_here python=3.8
conda activate new_name_here

Then, install the required packages using conda and pip. Ensure that you 
have activated the environment before proceeding with this step.
conda install -c conda-forge ffmpeg=5.1.2 ipython=8.11.0 ipywidgets=8.0.4 \
  jupyterlab=3.6.1 matplotlib=3.7.1 numpy=1.24.2 onnx=1.13.0 pillow=9.4.0 pip=23.0.1


For CUDA support, verify your CUDA version:
nvcc --version  # Example: release 11.8 = 11.8, release 12.1 = 12.1

Then install PyTorch with the appropriate CUDA version:
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia 

For full compatibility with the reinforcement learning framework, ensure the following packages are installed:
pip install swig box2d-py==2.3.5 decorator==4.4.2 gymnasium==0.29.0 imageio==2.26.0 \
  imageio-ffmpeg==0.4.8 moviepy==1.0.3 onnx2pytorch==0.4.1 opencv-python==4.7.0.72 \
  protobuf==4.22.1 pygame==2.1.3.dev8 tqdm==4.65.0 wandb==0.14.0


3. Verifying the Installation

To verify that all packages have been installed successfully, run:
python -m pip list

This will list all the currently installed packages in your environment, allowing you to ensure 
that all dependencies are there.


4. Additional Notes

If any package is missing or incompatible, refer to the environment_windows.yml or environment_ubuntu.yml file
for the complete list of dependencies.
If you encounter issues, please report them in the Moodle forum.
