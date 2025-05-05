## Setting up your Environment

For this course, you will need `python 3` (which is something different than `python 2`!).
The required packages to run all assignment code are listed in `requirements.txt`.
This gives you essentially two options to set up your environment:

 1. Install python and/or pip by following e.g. [this tutorial](https://packaging.python.org/tutorials/installing-packages).
  If you also want to have CUDA support (see below), you will also need to install the 
  [CUDA toolkit](https://developer.nvidia.com/cuda-downloads). Then simply run
   
   ```
   pip install -r requirements.txt
   ```

 2. Install [anaconda](https://docs.anaconda.com/anaconda/install/) 
 (or [miniconda](https://docs.conda.io/en/latest/miniconda.html) if you do not like bloated software) and run
   
   ```
   conda create -n dlnn2 python>=3.7 pytorch-cuda=11.6 --file requirements.txt -c pytorch -c nvidia
   ```
   
   if you want to have CUDA support or just
   
   ```
   conda create -n dlnn2 python>=3.7 --file requirements.txt -c pytorch
   ```
   
   if you do not have/need a GPU (see [pytorch instructions](https://pytorch.org/get-started/locally) for further details).

Once the packages have been installed, it should be possible to start a notebook server as follows

```
jupyter notebook
```
This will normally open a browser window, in which you can see the contents of your current directory.
If you start this command in the directory where you have your assignment notebooks,
you will be able to open them and start working on them.

## Using GPUs

Deep Learning is a compute-intensive business. 
Although the course is designed in such a way that it requires as little resources as possible,
there are some exercises where you will have to compute on a GPU,
or at least benefit greatly if a GPU is available.

If you have a GPU of
 - Nvidia with sufficient [CUDA capability](https://developer.nvidia.com/cuda-gpus#compute),
you are in luck and should be able to run everything locally.
 - AMD, it would have to be supported by [ROCm](https://rocm.github.io/install.html#hardware-support)
and it requires you to [build pytorch manually](https://github.com/pytorch/pytorch/issues/10657#issuecomment-415067478),
i.e. without using the *conda* or *pip* commands above.
Even if you manage to set up pytorch with ROC, full support is not guaranteed.
 - Intel, it will probably take some time for libraries to catch up (as of Feb 2021),
 but my guess is that you will want to look out for [oneAPI](https://github.com/pytorch/pytorch/issues/30029) support(?). 
 Integrated graphics are not supported by DL libraries (to the best of my knowledge).

##### Google Colab

If you do not have a GPU or if you do not manage to get things to work,
we advise to use [Google Colab](https://colab.research.google.com). 
Colab is a notebook server hosted by Google,
which provides access to GPUs and TPUs (for **free**). 
It uses those GPUs that are currently not in use by any of the paid customers, 
which means that long runs can be interrupted if the GPUs would be needed again.
When using colab notebooks too much, you can also be denied GPUs.
Take a look at the [colab FAQ](https://research.google.com/colaboratory/faq.html#resource-limits)
for more information on the resource limits.

The assignment notebooks can simply be uploaded to Colab,
edited and executed in the online editor,
and then downloaded again as `.ipynb` notebooks to be submitted to Moodle.
Since Colab does not support the `raw` cell type,
the copyright statement will not render in Colab,
but this should not affect the notebooks in any way.

In order to use hardware acceleration in Colab notebooks,
you navigate to *Edit > Notebook settings* 
or *Runtime > Change runtime type* in the menu
and then you can select *GPU* under *Hardware accelerator*.
To test whether the GPU has been made available, 
you can execute the following code snippet in the notebook:
```python
import torch
torch.cuda.is_available()
```

NOTE that colab is merely a suggestion for a GPU-providing service. 
Feel free to use any services that you are familiar with or want to try out.
If you have good experiences with other **free**(mium) services,
you can also let fellow students (and myself) know in the forum.
