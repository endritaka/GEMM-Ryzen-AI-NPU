# GEMM Optimization on Ryzen AI NPUs

This repository contains some parts of the code for work "Striking the Balance: GEMM Performance Optimization Across Generations of Ryzen AI NPUs" which was accepted at ISFPGA 2026 as a poster ([https://dl.acm.org/doi/abs/10.1145/3706628.3708867](https://arxiv.org/abs/2512.13282)).

## Repository structure

- `micro-benchmarking/`
  This folder contains multiple micro-benchmarking tests used to identify DDR bandwidth for the Ryzen AI NPU platform.

  The experiments include:

  - Contiguous data transfer tests to measure baseline DDR bandwidth
  - GEMM-inspired transfer patterns that imitate the memory movement of GEMM workloads and estimate the effective DDR bandwidth when executing GEMM

  These tests are used to estimate the effective DDR bandwidth seen when running GEMM on the NPU, not just the peak bandwidth under ideal contiguous accesses.

- `XDNA_GEMM_kernels/`
  This folder contains the optimized GEMM kernels and configurations for the `int8`, `int16`, and `bf16` data types. These kernels reflect the selected configurations after optimization through analytical modeling.

- `multi_core_GEMM/`
  This folder contains the optimized GEMM mapping code for execution across the whole NPU array, along with scripts for GEMM performance sweeps and roofline plot generation.
