# SciPy 2023 tutorial: Thinking in arrays

This repository contains everything you need to follow the "[Thinking in arrays](https://cfp.scipy.org/2023/talk/XBUC8S/)" tutorial, presented at the [SciPy 2023](https://www.scipy2023.scipy.org/) conference on [Tuesday, July 11, 2023 at 8:00am‒12:00pm CDT](https://www.scipy2023.scipy.org/schedule) in [Classroom 103](https://meetattexas.com/floorplans#m1).

<br>

**Abstract:**

Despite its reputation for being slow, Python is the leading language of scientific computing, which generally needs large-scale (fast) computations. This is because most scientific problems can be split into "metadata munging" and "number crunching," where the latter is performed by array-oriented (vectorized) calls into precompiled routines.

This tutorial is an introduction to array-oriented programming. We'll focus on techniques that are equally useful in NumPy, Pandas, xarray, CuPy, Awkward Array, and other libraries, and we'll work in groups on three class projects: Conway's Game of Life, evaluating decision trees, and computations on ragged arrays.

Array-oriented programming is a paradigm in its own right, challenging us to think about problems in a different way. From APL in 1966 to NumPy today, most users of array-oriented programming are scientists, analyzing or simulating data. This tutorial focuses on the thought process: all of the problems are to be solved in an imperative way (for loops) and an array-oriented way. Matlab will be used for plotting, but all plotting commands will be given (not prerequisites).

We'll alternate between short lectures and small group projects (3‒4 people each), in which tutors will be available for help, followed by a guided tour through solutions, alternatives, and trade-offs.

<br>

## Prerequisites

You should have a basic familiarity with NumPy, such as the content of the "[Introduction to Numerical Computing With NumPy](https://cfp.scipy.org/2023/talk/UJBWPQ/)" tutorial.

This tutorial consists of interactive lectures and exercises, all of which run in Jupyter notebooks. These notebooks depend on the libraries listed in [environment.yml](environment.yml). On the day of the tutorial, we will use Quansight's Nebari platform to run the notebooks in the cloud with all dependencies installed. See

<h3 align="center"><a href="https://docs.google.com/document/d/1vnWhNyUBRpILb2MAHQfTmZQY3pCIaCmroV9ke49nQlE/edit?usp=sharing">Nebari instructions</a></h3>

to get started.

You can also install the packages on your personal computer. If you're accessing this after the day of the tutorial, this is the only way to do it (Nebari won't be available), but if it's the day of the tutorial, Nebari is strongly preferred. We won't take any tutorial time to solve installation problems.

<br>

### Running the notebooks on your personal computer

If you have some version of conda/mamba/Anaconda/Miniconda/Miniforge, you can install the [environment.yml](environment.yml) as a new environment, then activate that environment and run JupyterLab.

If you're new to this package manager, we recommend the mamba/CPython version of [Miniforge](https://github.com/conda-forge/miniforge), which has [detailed instructions here](https://scikit-hep.org/user/installing-conda).

Once conda/mamba is installed, the command to [create an environment from a file](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file) is

```bash
wget https://raw.githubusercontent.com/jpivarski-talks/2023-07-11-scipy-tutorial-advanced-numpy/main/environment.yml
conda env create -f environment.yml   # can replace "conda" with "mamba"
```

The command to [activate that environment](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#activating-an-environment) (once per terminal) is

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

<br>

## Roadmap for following the tutorials

In each directory, [part-1](part-1), [part-2](part-2), and [part-3](part-3), there are four notebooks:

  * **lecture-slides:** the presentation, to be viewed in [jupyterlab-deck](https://jupyterlab-deck.readthedocs.io/)
  * **lecture-workbook:** for participants to use during the lecture; acts as a scratch-pad for solving "quizlets"
  * **project:** a larger exercise to work on after each lecture
  * **solutions:** discussion of different ways to solve the exercise.

During the live tutorial, participants should open the **lecture-workbook**. The **lecture-slides** will be projected on a big screen. Offline, after the event, open both notebooks and read through the **lecture-slides**.

When everyone is working on exercises, I'll share

<h3 align="center"><a href="https://app.sli.do/event/mAiL1wgxpBXyTrRFTEsC94/embed/polls/da924656-e37b-4aa8-828c-90d7faa58915">this Slido link</a></h3>

to follow your progress. It should take you to a page that looks like this:

<p align="center"><picture><img src="https://github.com/jpivarski-talks/2023-07-11-scipy2023-tutorial-thinking-in-arrays/assets/1852447/1603b323-fb27-4023-a1ed-7e2c979c7669"></picture></p>

## Timeline of the tutorials

**0:00‒0:20 (20 min):** Part 1 lecture: array-oriented programming as a paradigm: APL, SPEAKEASY, IDL, MATLAB, S, R, NumPy. Overview of basic and advanced slicing, broadcasting, and dimensional reduction. Powerful concept: element indexing is function application and advanced slicing is function composition.

**0:20‒0:40 (20 min):** Project 1: Conway's Game of Life. Calculating number of neighbors and updating the board "all at once."

**0:40‒0:55 (15 min):** Break

**0:55‒1:15 (20 min):** Guided discussion of solutions to Project 1.

**1:15‒1:35 (20 min):** Part 2 lecture: array-oriented programming and the "iteration until converged" problem. How to update arrays in which some elements have converged and others haven't.

**1:35‒1:55 (20 min):** Project 2: evaluating a decision tree, by walking over each node individually (as in a computer science class) and by million-ball Plinko! (how Scikit-Learn actually does it).

**1:55‒2:10 (15 min):** Break

**2:10‒2:40 (30 min):** Solutions to Project 2.

**2:40‒3:00 (20 min):** Part 3 lecture: non-rectilinear (ragged) arrays and arrays of arbitrary data structures: Apache Arrow and Awkward Array.

**3:00‒3:25 (25 min):** Project 3: a big, ragged dataset: computing lengths of taxi trips from polylines with varying numbers of edges. Since this is a big dataset, we'll also look at ways to scale it up with Dask.

**3:25‒3:40 (15 min):** Break

**3:40‒4:00 (20 min):** Solutions to Project 3.
