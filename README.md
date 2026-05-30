modANTLite: Modular Advanced Neural Training Framework

PROJECT STATUS: ACTIVE WORK IN PROGRESS

Please note: modANTLite is currently in an active development phase. While the core Python simulation modules, dynamic model compilation, and SQLite telemetry logging are stable, advanced systems such as C++/CUDA bindings, MPI multi-node scaling, physical sensor fusion bridges (RAPTOR), and bare-metal compilation pipelines are undergoing continuous architectural integration and testing.

Executive Summary

modANTLite is a professional, research-grade machine learning and avionics simulation suite. It is engineered to bridge the critical gap between theoretical neural network topology and physical hardware constraints.

The framework eschews black-box training in favor of deterministic hardware profiling. It allows researchers to procedurally generate complex neural architectures, simulate their execution bounds, and visualize resource bottlenecks across a diverse spectrum of hardware fabrics—ranging from edge AI clusters (e.g., NVIDIA Jetson AGX Orin) and unified memory APUs (e.g., AMD Ryzen AI Max+ 395) to massive discrete enterprise GPU arrays. By calculating exact memory bandwidth limitations, interconnect latencies, and theoretical floating-point operations per second (TFLOPS), modANTLite ensures that topological design is strictly grounded in physical reality.

Core System Architecture

Synaptic Orchestrator

The foundation of the framework is a multiprocessing supervisor that governs the neural simulation core alongside system telemetry. It actively monitors hardware health and features a real-time Thermal Watchdog that interfaces directly with physical system-on-chip (SOC) temperatures. It dynamically throttles or interrupts simulation workloads if hardware exceeds critical thermal thresholds, ensuring hardware safety during intense theoretical compute cycles.

Global Hardware Topology Manager

A global state engine that manages the abstraction between the software operations and the physical hardware profile. It utilizes an OS-level modification-time cache to eliminate non-volatile memory (NVMe) I/O thrashing during high-frequency read loops. This manager permits real-time hot-swapping of the simulated execution environment; changing the global node instantly updates the mathematical constraints across the entire framework to reflect the new VRAM ceilings, PCIe/NVLink bandwidth limits, and multi-node geometries.

M.A.R.S. Experiment Tracker

An embedded, ACID-compliant SQLite telemetry database utilizing Write-Ahead Logging (WAL) and concurrent timeout structures. This guarantees safe, non-blocking writes from distributed multiprocessing nodes. It permanently tracks hyperparameter matrices, hardware hashes, and granular loss/accuracy progressions, permitting researchers to retroactively render terminal-based spectrograms of previous training runs.

Central Model Registry

A persistent, disk-based artifact manager. Models compiled within the Advanced Builder are serialized as JSON configuration blueprints and PyTorch state dictionaries. The registry enforces a strict Architectural Lockout Mechanism; when sub-sectors request a custom model for physical profiling, the registry mathematically filters the available artifacts to ensure geometric compatibility (e.g., preventing a Convolutional Neural Network from being loaded into a Sequence-based RLHF memory profiler).

The Advanced Model Builder

The framework features a dynamic, procedural architecture compiler that allows researchers to construct neural manifolds from the ground up and execute synthetic training simulations.

Phase 1: Architectural Blueprinting: Supports the dynamic generation of Multi-Layer Perceptrons (MLP), Convolutional Neural Networks (CNN), Long Short-Term Memory recurrent networks (LSTM), and Attention-based Transformer encoders. Supports configurable layer depths, multi-head dimensions, and normalization algorithms.

Phase 2: Hyperparameter Matrix: Exposes granular control over stochastic optimization engines (AdamW, SGD, RMSProp), learning rate schedules, weight decay regularization, and objective loss functions (Cross-Entropy, MSE, Huber).

Phase 3: Pre-Flight Hardware Verification: Automatically derives the necessary tensor shapes based on the active hardware. The engine allocates a synthetic tensor to the appropriate device (CUDA or CPU) and executes a dry-run forward pass. This validates mathematical stability and calculates the precise megabyte footprint against the globally selected hardware fabric prior to execution.

Phase 4: Active Training Simulation: Executes a localized training loop bounded by the predefined geometry, logging all metrics to the M.A.R.S database, and subsequently saving the validated model to the Central Registry for advanced analysis in specialized sectors.

Detailed Research Sectors & Mathematical Profiling

modANTLite calculates the physics of machine learning. Below is an exhaustive breakdown of the available simulations and their underlying mathematical profiling objectives.

Sector 1: Frontier Architectures

1.1 Distributed Frontier Training

5D Parallelism Matrix Topology Profiler: Simulates massive-scale model sharding across Data, Tensor, Pipeline, Context, and Expert parallelism dimensions. It calculates the exact VRAM footprint required per device when splitting weights, gradients, and optimizer states across distributed interconnects.

Virtual Interleaved 1F1B Pipeline Bubble Tracker: Calculates synchronous pipeline inefficiencies. It contrasts the computational idle time ("bubbles") of standard 1-Forward-1-Backward pipelining against virtualized, non-contiguous chunking strategies, projecting exact cluster throughput recovery percentages.

MFU & Arithmetic Execution Intensity Profiler: Derives the true Model FLOPs Utilization (MFU). It calculates the total arithmetic operations required per token under full activation recomputation and contrasts the attained speed against the theoretical peak TFLOPS of the selected hardware.

Hierarchical Tiered Communication Sharding (FSDP2): Evaluates the bandwidth efficiency across heterogeneous network layers (intra-node NVLink vs. inter-node InfiniBand), demonstrating how quantized gradient compression eliminates serialization delays across physical domain boundaries.

1.2 Generative Adversarial Networks (GAN)

Wasserstein GAN w/ Gradient Penalty (WGAN-GP): Simulates the minimization of the Earth Mover's Distance. It profiles the stability of the critic network by enforcing 1-Lipschitz continuity, calculating the mathematical penalty applied when gradient norms deviate from a strict 1.0 constraint.

StyleGAN Latent Space Mapping (Z -> W): Evaluates the VRAM requirements for high-resolution target synthesis. It simulates the mapping of a normally distributed Z-space through a multi-layer perceptron into an intermediate W-space, demonstrating the reduction in feature entanglement as measured by Perceptual Path Length (PPL).

1.3 Diffusion Models

DDPM Forward/Reverse Process: Simulates the Reverse Markov Chain denoising schedule. It tracks the dynamic Signal-to-Noise Ratio (SNR) and isotropic Gaussian noise subtraction over a defined timestep matrix.

Latent Diffusion / VAE Compression: Quantifies spatial reduction. It compares the raw megabyte footprint of high-resolution pixel tensors against compressed latent representations output by a Variational Autoencoder, projecting the resulting reduction in memory bandwidth saturation.

1.4 NLP & LLM Training

Supervised Fine-Tuning (SFT): Simulates standard causal language modeling minimization. It profiles learning rate decay schedules (cosine annealing) and the inverse relationship between Cross-Entropy loss reduction and text perplexity metrics.

Direct Preference Optimization (DPO): Simulates policy alignment without explicit reward models. It computes an implicit reward margin using a binary cross-entropy objective, tracking the divergence penalty between chosen and rejected probability distributions.

1.5 Scientific Machine Learning

Physics-Informed Neural Networks (PINNs): Simulates convergence on physical laws (e.g., the 1D Burgers' Equation for fluid mechanics). It profiles the dual-optimization objective where the network minimizes both empirical data loss and the underlying differential equation residual loss simultaneously.

Fourier Neural Operator (FNO): Evaluates infinite-dimensional operator learning in the spectral domain. It calculates the memory cost and convolution constraints required to execute Fast Fourier Transforms while truncating high-frequency modes to preserve VRAM.

1.6 Quantum Machine Learning

Variational Quantum Circuits (VQC): Calculates the exponential memory boundaries inherent to simulating entangled quantum states on classical hardware. It verifies whether the O(2^N) complex amplitudes required for a specified qubit count will trigger an Out-Of-Memory fault on the currently selected hardware profile.

1.7 Frontier Transformer Architectures

Multi-Head Latent Attention (MLA): Evaluates the DeepSeek V3/R1 attention mechanism. It calculates the exact VRAM bandwidth saved by decoupling rotary position embeddings (RoPE) and compressing the standard KV-Cache into a shared latent vector space during autoregressive decoding.

Infinite Streaming KV-Cache (Attention Sinks): Models O(1) constant memory bounds. It demonstrates how anchoring the initial tokens of a sequence while utilizing a rolling contextual window prevents the standard O(N) memory collapse during infinite context generation.

Mixture of Depths (MoD): Simulates strict computational capacity constraints. It profiles dynamic FLOP routing where low-salience tokens bypass computation blocks via residual connections, capping global computational load below maximum hardware limits.

Test-Time Compute (MCTS & UCB1): Evaluates System 2 reasoning trajectories. It simulates Monte Carlo Tree Search node expansion scored by a Process Reward Model, utilizing Upper Confidence Bounds to traverse hypothesis states before generating terminal sequences.

Test-Time Training (TTT) Layers: Profiles the replacement of standard KV-caches with constant-memory inner models. It simulates real-time gradient descent during the forward pass, mapping hidden state updates driven by a self-supervised learning objective.

1.8 Asynchronous Swarm & MPI Orchestration

Distributed Low-Communication (DiLoCo): Simulates outer-loop optimization across edge nodes separated by high-latency internet connections. It contrasts local inner-compute TFLOPS time against the severe latency penalties of synchronizing gradients over simulated standard WAN bandwidth.

MPI / NCCL Ring-AllReduce: Calculates the exact physical transfer times of symmetric gradient synchronization. It models the Scatter-Reduce and All-Gather algorithmic phases against the specific gigabytes-per-second constraints of the active hardware interconnect.

Sector 2: Optimization & AutoML

2.1 Model Pruning Lab

Wanda (Weight x Activation): Profiles post-training structural sparsity. It simulates weight masking by calculating the Hadamard product of weight magnitudes and input activation norms, bypassing the need for retraining.

RigL (Rigged Lottery / Dynamic Sparse Training): Evaluates dynamic topology shifting. It tracks the iterative dropping of low-magnitude connections and the localized growing of new connections based on maximum gradient vectors, all while maintaining a rigid overall sparsity percentage.

2.2 Quantization & Compression

Activation-Aware Weight Quantization (AWQ): Calculates memory bandwidth un-bottlenecking. It demonstrates the throughput advantages of identifying salient structural channels to retain in high precision while compressing the remaining tensor mass to 4-bit integers.

Quantization-Aware Training (QAT): Simulates the injection of artificial quantization noise during the forward pass. It profiles how networks adapt to INT8 degradation via Straight-Through Estimators (STE) applied to the backward gradient pass.

2.3 Hyperparameter Optimization Lab

Population Based Training (PBT): Simulates evolutionary hyperparameter synchronization. It evaluates the total hardware VRAM required to host multiple parallel worker models, tracking the mutation and exploitation of optimal scheduling parameters across discrete generations.

Asynchronous Successive Halving (ASHA): Profiles aggressive hyperband resource allocation. It models the periodic termination of underperforming network configurations to dedicate maximum computational budget to optimal topologies.

2.4 Neural Architecture Search (NAS)

Differentiable Architecture Search (DARTS): Evaluates continuous supernet optimization. It tracks the gradient-based alteration of operation mixing weights (alpha variables) prior to deriving a discrete sub-network topology via argmax operations.

Zero-Cost Proxies (Synflow): Models the theoretical scoring of networks at initialization time (t=0). It evaluates Jacobian covariance matrices to rank the expressivity of random architectures instantaneously without requiring backpropagation or training loops.

Sector 3: Meta & Dynamic Systems

3.1 RLHF & Alignment

Proximal Policy Optimization (PPO): Evaluates the extreme memory demands of standard reinforcement learning from human feedback. It computes the 4x VRAM overhead necessary to host the Actor, Critic, Reward, and Reference models simultaneously, evaluating the KL-divergence penalty constraints during policy updates.

Reward Modeling: Simulates the initialization of scalar reward functions from human pairwise preferences. It tracks the minimization of the negative log-likelihood across chosen versus rejected response trajectories utilizing Bradley-Terry mathematical principles.

3.2 Mixture of Experts (MoE)

Expert Routing (Top-K Capacity): Profiles the decoupling of resident memory size from active compute latency. It calculates the difference in VRAM required to host massive multi-expert manifolds versus the actual FLOPs utilized when a gating network routes specific tokens to a sparse Top-K selection.

Load Balancing (Auxiliary Loss): Simulates gating collapse and recovery. It models the requisite auxiliary loss penalties mathematically required to prevent a network from disproportionately routing all tokens to a single expert, ensuring uniform cluster utilization.

3.3 Active Learning & Harvesting

Uncertainty Sampling (Shannon Entropy): Evaluates data-pool isolation for Human-In-The-Loop pipelines. It calculates the probability distribution variance across unlabelled data, leveraging Shannon Entropy calculations to automatically quarantine the samples presenting the highest mathematical uncertainty.

Dynamic Custom Model Profiling (Registry Integration)

A defining feature of the modANTLite framework is the pervasive integration of the Central Model Registry. Within nearly every aforementioned sector, researchers possess the capability to load architectures generated in the Advanced Model Builder and subject them to theoretical physical analysis.

By injecting real PyTorch tensors through custom topologies, the framework automatically derives precise VRAM inference requirements, parameter counts, theoretical milliseconds of latency, post-quantization memory footprints, structural sparsity masks, and instantaneous Zero-Cost proxy evaluations.# modANT_Modular-Advanced-Neural-Trainer
README.md about a system written in python that simulations various types of neural networks.
