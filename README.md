# Putting Dynamics First: State-Space Modelling for Human Neuroscience
Tutorial materials for a Keynote&Tutorial at CCN2026 (New York).

There are 3 core notebooks:
1. [02] introduction to Kalman Filtering (dynamax/python)
2. [02] fitting LDS models to synthetic data (dynamax/python)
2. [02*_R] same as 02, in R (MARSS/R)
3. [03] fitting SLDS models to HCP data (StateSpaceDynamics.jl/julia)

To run locally:
- the python environment is managed using uv ([install](https://docs.astral.sh/uv/getting-started/installation/); from a terminal at the folder: `uv sync`)
- the julia environment is managed by the julia package manager ([install](https://julialang.org/downloads/); from a terminal at the folder: start julia: `julia`, switch to package manager:  `]`, setup package: `instantiate .`) 
