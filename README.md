# Putting Dynamics First: State-Space Modelling for Human Neuroscience
Materials for the CCN2026 Tutorial (New York)
Kimmel Center, Grand Hall @ 4:30pm

**Harrison Ritz & Luiz Pessoa**


State-space models (SSMs) treat a recording as a *latent trajectory* evolving in time rather than as a
bag of trials or a static connectivity matrix. This tutorial builds that view from the ground up: exact
inference in linear-Gaussian SSMs (the Kalman filter), learning parameters by EM and the identifiability
traps that come with it, and finally switching models that segment task fMRI into discrete dynamical
regimes without ever seeing the task.

**Prerequisites:** linear algebra (eigenvalues, matrix factorizations) and basic probability
(Gaussians, conditioning). Some familiarity with Python is enough to follow all three notebooks — no
prior experience with R, Julia, or state-space modelling is assumed.

### [Slides](2026_CCN-tutorial.pdf)

## Notebooks

Three core notebooks, each runnable on Google Colab (with a Google account) or locally.
**On Colab, set the runtime language first** — *Runtime → Change runtime type* — as noted per
notebook below; the badge always opens a Python runtime by default.

1. [**01**](01_kalman_filter_information_form.ipynb) — introduction to Kalman filtering
   (Python / [dynamax](https://github.com/probml/dynamax)); Colab runtime: **Python**
   <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/01_kalman_filter_information_form.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

2. [**02**](02_lds_parameter_recovery.ipynb) — fitting LDS models to synthetic data, and what
   "recovery" does and doesn't mean. Two equivalent versions:
   - Python / [dynamax](https://github.com/probml/dynamax); Colab runtime: **Python**
     <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/02_lds_parameter_recovery.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
   - [R](02_lds_parameter_recovery_R.ipynb) / [MARSS](https://github.com/atsa-es/MARSS); Colab runtime: **R**
     <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/02_lds_parameter_recovery_R.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

3. [**03**](03_switching_lds_fmri_hcp.ipynb) — fitting SLDS models to HCP task fMRI
   (Julia / [StateSpaceDynamics.jl](https://github.com/depasquale-lab/StateSpaceDynamics.jl));
   Colab runtime: **Julia**
   <a href="https://colab.research.google.com/github/harrisonritz/DynamicsTutorial_CCN2026/blob/main/03_switching_lds_fmri_hcp.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

   > **Run the setup cells early.** Notebook 3 precompiles a sizeable Julia environment (several
   > minutes on a fresh Colab runtime) and downloads ~13 MB of assets — the parcellated HCP tensors,
   > the Schaefer-100/17 atlas, and the fsLR-32k surfaces — into `derivatives/`.

## Running locally

Clone the repo:

```sh
git clone https://github.com/harrisonritz/DynamicsTutorial_CCN2026.git
cd DynamicsTutorial_CCN2026
```

Then set up whichever language(s) you need — the three notebooks are independent.

### Python (notebooks 01, 02)

Managed with [`uv`](https://docs.astral.sh/uv/getting-started/installation/), which installs the
right Python version for you (the project needs ≥ 3.14):

```sh
uv sync                 # create the environment
uv run jupyter lab      # launch, then select this environment's Python 3 kernel
```

### R (notebook 02_R)

Install [R](https://cran.r-project.org/), then from an R session:

```r
install.packages(c("MARSS", "MASS", "IRkernel"))
IRkernel::installspec()   # registers the R kernel with Jupyter
```

The notebook also installs `MARSS`/`MASS` itself if they are missing, so on Colab you only need to
switch the runtime to R.

### Julia (notebook 03)

Install [Julia](https://julialang.org/downloads/) (the checked-in `Manifest.toml` was resolved on
1.13). From a terminal at the repo folder:

```zsh
julia --project=.   # start Julia *in this project's environment*
```

Install the dependencies (takes a few minutes):

```julia
using Pkg
Pkg.instantiate()   # install dependencies from Manifest.toml
```

Then register the Jupyter kernel and open the notebook (`IJulia` is already a dependency):

```julia
using IJulia
notebook(dir = ".")
```

## Data

The HCP tensors used in notebook 3 are not stored in this repo — the notebook downloads them, along
with the atlas and surface files, into `derivatives/` (gitignored). They are Schaefer-100 / Yeo-17
parcellated timeseries from the HCP `LANGUAGE` task: 43 subjects × 2 runs, T = 316 TRs at TR = 0.72 s.

Data were provided by the Human Connectome Project, WU-Minn Consortium (Principal Investigators:
David Van Essen and Kamil Ugurbil; 1U54MH091657), funded by the 16 NIH Institutes and Centers that
support the NIH Blueprint for Neuroscience Research, and by the McDonnell Center for Systems
Neuroscience at Washington University. Use of these derivatives is subject to the
[HCP Open Access Data Use Terms](https://www.humanconnectome.org/study/hcp-young-adult/document/wu-minn-hcp-consortium-open-access-data-use-terms).

## Further reading

- [dynamax](https://probml.github.io/dynamax/) — JAX state-space models (notebooks 01–02)
- [MARSS](https://atsa-es.github.io/MARSS/) — multivariate autoregressive state-space models in R
- [StateSpaceDynamics.jl](https://github.com/depasquale-lab/StateSpaceDynamics.jl) — SSMs in Julia
- Murphy, *Probabilistic Machine Learning: Advanced Topics* (2023), ch. 8–9 — inference and learning in SSMs

## License, citation, and contact

Code and materials are released under [GPL-3.0](LICENSE). If you use these materials, please cite the
tutorial: Ritz, H. & Pessoa, L. (2026). *Putting Dynamics First: State-Space Modelling for Human
Neuroscience.* Tutorial at the Conference on Cognitive Computational Neuroscience (CCN), New York.

Questions, or something not running? Please
[open an issue](https://github.com/harrisonritz/DynamicsTutorial_CCN2026/issues).
