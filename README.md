# AD-SWD

**Automatic Differentiation Skeletonized Wave-Equation Dispersion Inversion**

A PyTorch-based framework for differentiable, extensible skeletonized wave-equation dispersion inversion (SWD) of ambient-noise surface waves.

> **Status:** The accompanying paper is in preparation. The full implementation, examples, and documentation will be released in this repository after the paper is accepted. This repository currently contains only this README.

## Paper

**Title:** An Extensible Skeletonized Wave-Equation Dispersion Inversion Framework with Automatic Differentiation for Urban Traffic Noise Imaging (IEEE TGRS, in preparation)

**Authors:** Weishuai Chang, Guangzhou Shao, and Keyu Huo



## Planned repository structure

```text
AD-SWD/
├── swd_python/        # core: forward modeling, Radon transform, picking, inversion
├── swd_aux/           # hand-derived gradient reference and auxiliary tools
├── notebooks/         # synthetic and field-data examples
├── configs/           # example parameter files
├── docs/              # installation, configuration, and reproduction notes
├── tests/             # unit tests and gradient checks
└── README.md
```

## Method at a glance

For a velocity model $\mathbf{m}$, the graph is

$$
\mathbf{m} \;\rightarrow\; \mathbf{w} \;\rightarrow\; D \;\rightarrow\; \kappa \;\rightarrow\; \epsilon,
$$

where $\mathbf{w}$ is the predicted seismic data, $D$ is the dispersion spectrum, $\kappa$ is the picked dispersion curve, and $\epsilon$ is the misfit. PyTorch AD backpropagates through the chain from $\mathbf{w}$ to $\epsilon$; Deepwave supplies the gradient of $\mathbf{w}$ with respect to $\mathbf{m}$ through its adjoint-state backward. The result is the model gradient without manual construction of the SWD-specific adjoint source.

## Requirements (planned)

- Python 3.9+
- PyTorch 2.x
- Deepwave
- NumPy, SciPy, Matplotlib
- CUDA-capable GPU

## Contact

- Weishuai Chang — changweishuai26@stu.pku.edu.cn
- Guangzhou Shao — shao_gz@chd.edu.cn (corresponding author)


## Acknowledgments

The implementation builds on [Deepwave](https://github.com/ar4/deepwave) and [PyTorch](https://pytorch.org/). We thank the developers for making these tools available.
