# SciPy 2023 tutorial: Thinking in arrays

This repository contains everything you need to follow the "[Thinking in arrays](https://cfp.scipy.org/2023/talk/XBUC8S/)" tutorial, presented at the [SciPy 2023](https://www.scipy2023.scipy.org/) conference on [Tuesday, July 11, 2023 at 8:00am‒12:00pm CDT](https://www.scipy2023.scipy.org/schedule) in [Classroom 103](https://meetattexas.com/floorplans#m1).

**Abstract:**

Despite its reputation for being slow, Python is the leading language of scientific computing, which generally needs large-scale (fast) computations. This is because most scientific problems can be split into "metadata munging" and "number crunching," where the latter is performed by array-oriented (vectorized) calls into precompiled routines.

This tutorial is an introduction to array-oriented programming. We'll focus on techniques that are equally useful in NumPy, Pandas, xarray, CuPy, Awkward Array, and other libraries, and we'll work in groups on three class projects: Conway's Game of Life, evaluating decision trees, and computations on ragged arrays.

## Prerequisites

Participants should have a basic familiarity with NumPy, such as the content of the "[Introduction to Numerical Computing With NumPy](https://cfp.scipy.org/2023/talk/UJBWPQ/)" tutorial.

This tutorial consists of interactive lectures and exercises, all of which are implemented in Jupyter notebooks. These Jupyter notebooks depend on the libraries listed in [environment.yml](environment.yml).

The method of running the notebooks that we support is through GitHub Codespaces, which requires a GitHub account and either 8 remaining core-hours on your free account (see [your billing](https://github.com/settings/billing)) or a [paid plan](https://docs.github.com/en/billing/managing-billing-for-github-codespaces/about-billing-for-github-codespaces).

You can also install the packages on your personal computer ([see below](#running-the-notebooks-on-your-personal-computer)), but we can't help you with installation problems if you do it this way.

### Running the notebooks in Codespaces

1. Log into your GitHub account and open this page (this repo).

2. Launch a Codespace using the green buttons shown below. It will launch in a new tab.

<kbd><img src="https://github.com/jpivarski-talks/2023-07-11-scipy-tutorial-advanced-numpy/assets/1852447/9416081a-24b3-4d27-91ac-7143309cfcd1" width="100%"></img></kbd>

3. Wait a few seconds and it will automatically install the packages into your Codespace.

<kbd><img src="https://github.com/jpivarski-talks/2023-07-11-scipy-tutorial-advanced-numpy/assets/1852447/25f00392-0f66-4a49-8a54-a156b37b8eaf" width="100%"></img></kbd>

4. Package installation takes a few minutes, and high CPU utilization is expected. There is an option to watch the installation log (shown below).

<kbd><img src="https://github.com/jpivarski-talks/2023-07-11-scipy-tutorial-advanced-numpy/assets/1852447/d2f4aef8-a63e-41cb-b398-e306865139c1" width="100%"></img></kbd>

5. On the original browser tab (this page), you may need to reload to see the running Codespace. It will have a random, but memorable, name. Open its "..." menu and "Open with..." (shown below) to select "JupyterLab," which will launch in a new tab. If JupyterLab fails to launch the first time, try it again.

<kbd><img src="https://github.com/jpivarski-talks/2023-07-11-scipy-tutorial-advanced-numpy/assets/1852447/0cab351a-a476-4f1b-9417-713479f22465" width="100%"></img></kbd>

6. The Codespace will shut down if it's idle, but all of your changes are saved until you _delete_ the Codespace.

### Running the notebooks on your personal computer

If you have some version of conda/mamba/Anaconda/Miniconda/Miniforge, you can install the [environment.yml](environment.yml) as a new environment, then activate that environment and run JupyterLab.

If you're new to this package manager, we recommend the mamba version of [Miniforge](https://github.com/conda-forge/miniforge), which has [detailed instructions here](https://scikit-hep.org/user/installing-conda).

Once conda/mamba is installed, the command to [create an environment from a file](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file) is

```bash
wget https://raw.githubusercontent.com/jpivarski-talks/2023-07-11-scipy-tutorial-advanced-numpy/main/environment.yml
conda env create -f environment.yml   # can replace "conda" with "mamba"
```

The command to [activate that environment](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#activating-an-environment) is

```bash
conda activate 2023-07-11-scipy-tutorial-advanced-numpy
```

Get a copy of this repo and enter its directory.

```bash
git clone https://github.com/jpivarski-talks/2023-07-11-scipy-tutorial-advanced-numpy.git
cd 2023-07-11-scipy-tutorial-advanced-numpy
```

Start JupyterLab with

```bash
jupyter lab
```

It should attempt to open a browser tab to the Jupyter process running on your computer, and provides some URLs in the terminal in case that doesn't work.

## HERE
