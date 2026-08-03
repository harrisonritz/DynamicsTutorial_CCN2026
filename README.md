# Putting Dynamics First: State-Space Modelling for Human Neuroscience
Materials for the CCN2026 Tutorial (New York)

### [Slides](https://github.com/harrisonritz/DynamicsTutorial_CCN2026/blob/main/2026_CCN-tutorial.pdf) 

### There are 3 core notebooks, which can be run on Google Colab (with a Google account):
1. [01] introduction to Kalman Filtering (dynamax/python) <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/01_kalman_filter_information_form.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

2. [02] fitting LDS models to synthetic data (dynamax/python <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/02_lds_parameter_recovery.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a> 
or MARSS/R <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/02_lds_parameter_recovery_R.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>)
  
4. [03] fitting SLDS models to HCP data (StateSpaceDynamics.jl/Julia) <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/03_switching_lds_fmri_hcp.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

### To run these notebooks locally:
- clone the repo:
    ```sh
    git clone https://github.com/harrisonritz/DynamicsTutorial_CCN2026.git
    cd DynamicsTutorial_CCN2026
    ```
- the python environment is managed using `uv` 
  - [install uv](https://docs.astral.sh/uv/getting-started/installation/)
  - install environment: from a terminal at the repo folder: `uv sync`
- the Julia environment is managed by the Julia package manager 
  - [install julia](https://julialang.org/downloads/)
  - install environment: from a terminal at the repo folder:
    ```zsh
    julia           # start Julia
    ]               # switch to package manager
    instantiate     # install packages
    ```