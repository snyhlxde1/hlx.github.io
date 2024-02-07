# Accelerate LLM Inference with Few-Step Jacobi Decoding

**TL;DR:** In this article, we introduce consistency large language models (CLLMs), a new family models developed with our proposed techniques to reduce inference latency by efficiently decoding $n$ tokens in parallel. This decoding method is called [Jacobi decoding](https://arxiv.org/abs/2305.10427), which improve inference efficiency by breaking the seuqntially nature of convential auto-regressive (AR) decoding. CLLMs are trained with the objective of efficiently mapping any randomly initialized $n $-token sequence to a correctly predicted sequence in as few steps as possible. Experiment results show CLLMs obtained with our proposed method are highly effective, showing $1.3\times$ to $3.4\times$ improvements in generation speed while preserving generation quality in comparison with the baselines and other SOTA techniques. CLLMs also show a high adaptability and memory efficiency as they require no modifications to the existing model architecture and auxiliary model components.



## Background: Jacobi Decoding

Large language models (LLMs) are transforming the landscape of human lives, From programming to offering legal and health advice. However, during inference, LLMs generate responses token by token using AR decoding as shown in Figure 1, leading to high latency for longer responses. Using AR decoding, it often necessiate architectural modifications, auxiliary components, or draft models, to speedup inference by generating more than one token at a time. 

<p align="center"><img src="clm_objective.png" alt="autoregressive" width="250"></p>
<p align="center">Figure 1: illustration of conventional AR decoding: one token is generated at a time.</p>

[Jacobi decoding](https://arxiv.org/abs/2305.10427) originiates from the Jacobi and Gauss-Seidel fixed-point iteration for solving nonlinear equations, and is proven to be identical to AR generation using greedy decoding [[1]](https://proceedings.mlr.press/v139/song21a.html). reformulates the sequential generation process into a problem of solving a system of $n$ non-linear equations with $n$ variables. However, Jacobi decoding seldom accurately predicts more than one token in a single fixed-point iteration step.

<p align="center"><img src="jacobi_objective.png" alt="autoregressive" width="350"></p>
<p align="center">Figure 2: illustration of Jacobi decoding: n-token sequence is fed into the LLM and iterates until convergence.</p>

### Jacobi Trajectory

### Limitations of Vanilla Jacobi Decoding

## Consistency LLMs (CLLMs)

##  Experiments

### Fast Forwarding and Stationary Tokens

### Results


## Final words
We invite you to refer to the [our paper](TODO) for more details! Please stay tuned for code and CLLM checkpoint release!