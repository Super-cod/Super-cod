# Swayam Kapoor

**Systems & Compiler Software Engineer** | C++20 • Compilers & IR • GPU Architecture & PTX • Multimodal AI

[![GitHub Profile](https://img.shields.io/badge/GitHub-Super--cod-181717?style=flat&logo=github)](https://github.com/Super-cod)
[![Target Role](https://img.shields.io/badge/Focus-NVIDIA%20PTX%20Compiler%20%2F%20GPU%20Systems-76B900?style=flat&logo=nvidia)](https://github.com/Super-cod)
[![Silicon Verified](https://img.shields.io/badge/Verified%20On-NVIDIA%20RTX%203050%20(Ampere)-76B900?style=flat&logo=nvidia)](https://github.com/Super-cod)

---

## Technical Focus

Systems and compiler engineer specializing in **C++20 compiler frontends, 3AC intermediate representations, dataflow optimization passes, direct GPU programming via the NVIDIA PTX virtual ISA & Driver API, low-level microarchitecture & memory hierarchies, and from-scratch multimodal AI architectures**.

```
       ┌─────────────────────────────────────────────────────────────┐
       │                  Source Code (C++ / DSL)                    │
       └──────────────────────────────┬──────────────────────────────┘
                                      │
                      [ Lexer -> Parser -> AST -> Typecheck ]
                                      │
       ┌─────────────────────────────────────────────────────────────┐
       │               Intermediate Representation (IR)              │
       │  - 3-Address Code / Basic Blocks / Control Flow Graphs       │
       │  - Optimization Passes: Constant Folding, DCE, Algebraic    │
       └──────────────────────────────┬──────────────────────────────┘
                                      │
               ┌──────────────────────┴──────────────────────┐
               │                                             │
   [ Target: PTX Virtual ISA ]                  [ Target: Machine Code / Relocatables ]
   Direct nvcuda.dll JIT Driver                 Linkers, Relocations (PC-Rel Disp)
   Shared Memory Tiling & Coalescing            ELF64 / PE-COFF Binary Inspection
   Ampere SM 8.6 Hardware Silicon               CPUID, SIMD AVX2, Cache Line Padding
```

---

## Top 3 Featured Repositories (Pinned Showcase)

### 1. [ptx-toy-compiler](https://github.com/Super-cod/ptx-toy-compiler) — Modern C++20 Compiler & PTX Target
> **C++20 • Recursive Descent • 3AC IR • Constant Folding & DCE • PTX ISA Emitter • StackVM**
* **Frontend**: Hand-crafted recursive descent parser, lexical tokenizer with source location tracking, strongly-typed AST hierarchy, and symbol table with lexical scoping.
* **Intermediate Representation (IR)**: Linear three-address code (3AC) with virtual register allocation, basic block construction, and control-flow graphs.
* **Optimization Engine**: Iterative fixed-point dataflow optimization passes (constant folding, constant propagation, algebraic identity simplification, and dead code elimination).
* **Dual Backends**:
  1. Clean **PTX (Parallel Thread Execution) Emitter** generating valid NVIDIA virtual assembly (`.version 7.0`, `.target sm_75`, parameter registers, and predicated branches `@!%p0`). Emitted PTX verified to assemble and execute directly on NVIDIA silicon via `nvcuda.dll` `cuModuleLoadData`.
  2. In-memory **Stack Virtual Machine** bytecode interpreter for immediate test verification without requiring an external GPU driver.
* **Testing**: 12 automated unit and integration tests passing (`./build/ptxcc_tests`).

---

### 2. [cuda-kernel-perf-lab](https://github.com/Super-cod/cuda-kernel-perf-lab) — Direct PTX GPU Computing & Driver API
> **NVIDIA PTX Virtual ISA • Driver API (nvcuda.dll) • Shared Memory Tiling • Memory Coalescing • Warp Divergence**
* Direct interaction with NVIDIA GPU silicon (**GeForce RTX 3050 Laptop GPU, Ampere SM 8.6**) bypassing high-level CUDA runtime wrappers via raw PTX assembly JIT compilation:
  * **Shared Memory Tiling (GEMM)**: $16 \times 16$ SRAM tiles with `bar.sync 0` barriers, reducing global DRAM traffic by 16x and delivering **486 GFLOPS** (1.40x faster than naive DRAM streaming).
  * **Memory Coalescing**: Compares uncoalesced strided memory access against 128-bit vectorized `ld.global.v4.f32` transactions, achieving **175.14 GB/s throughput** (saturating 91% of the 128-bit GDDR6 memory bus).
  * **Warp Divergence**: Quantifies SIMT execution serialization penalty on divergent branches (**1.92x latency penalty** for divergent warps, matching theoretical 2x limit).
  * **Numerical Precision**: Verified against CPU reference calculations with floating-point tolerance ($\Delta < 10^{-5}$).
* Verified on physical NVIDIA RTX 3050 GPU via automated test runner (`.\run_experiments.ps1`).

---

### 3. [Multimodal-Vision-Language-Model-from-scratch](https://github.com/Super-cod/-Multimodal-Vision-Language-Model-from-scratch-in-PyTorch) — Vision-Language Model (VLM) Architecture
> **Vision Transformer (ViT) • Cross-Modal Linear Projector • Sequence Binding • Causal Language Decoder**
* End-to-end multimodal autoregressive architecture inspired by modern architectures (PaliGemma / LLaVA):
  * **Vision Encoder**: 2D Convolutional patch projection (16x16 patches, $N=196$), prepended learnable `[CLS]` token (197 tokens total), and stacked Pre-LN transformer encoder layers.
  * **Cross-Modal Projector**: Linear bottleneck projecting visual representations from latent vision space ($\mathbb{R}^{768}$) into textual representation space ($\mathbb{R}^{2048}$).
  * **Sequence Binding Engine**: Dynamic token sequence interleaving binding visual tokens into the text stream at designated `<image>` anchor positions.
  * **Causal Language Decoder**: Autoregressive decoding with Nucleus (Top-$p$) sampling.
  * Automated verification suite validating tensor shape contracts and end-to-end backpropagation gradients across all three sub-networks.
* Verified via automated shape and gradient flow test suite (`.\run_tests.ps1`).

---

## Supporting Systems & Architecture Laboratories

### 4. [Building_transformer_PyTorch](https://github.com/Super-cod/Building_transformer_PyTorch) — Transformer Decoder & Stateful KV-Cache
> **Autoregressive Inference • Stateful KV-Caching • Pre-LayerNorm • Causal Masking Invariance • RTX 3050 Benchmark**
* Clean implementation of the autoregressive Transformer Decoder architecture.
* Stateful Key-Value (KV) cache reducing generation complexity from $O(N^2)$ quadratic to $O(N)$ linear time.
* **Empirical GPU Benchmark (RTX 3050)**: KV-cache decoding achieves **196.0 tokens/sec** vs. **125.0 tokens/sec** for full-context recomputation (**1.57x throughput increase**).
* Automated verification of causal mask invariance ($\Delta = 0.000$) and KV-cache numerical equivalence ($\Delta < 4.77 \times 10^{-6}$).

### 5. [cpp-arch-perf-lab](https://github.com/Super-cod/cpp-arch-perf-lab) — Machine Architecture & Memory Hierarchy Lab
> **C++20 • CPUID Introspection • Cache Locality • Struct Padding • False Sharing • AVX2 SIMD**
* Empirical microbenchmark suite measuring hardware interactions with C++ systems:
  * **Spatial Cache Locality**: Measures a **7.39x throughput advantage** (5.56 GB/s Row-Major vs. 0.75 GB/s Column-Major) due to hardware cache line prefetching.
  * **Struct Alignment & Padding**: Demonstrates struct size reduction from 40 bytes to 24 bytes by sorting fields by alignment requirements (`offsetof` analysis, 40% memory reduction).
  * **False Sharing Elimination**: Eliminates multi-core MESI/MOESI bus invalidation ping-pong using `alignas(64)` cache line padding (**1.25x speedup**).
  * **Branch Prediction & CMOV**: Benchmarks branchless conditional moves against data-dependent branch mispredictions.
  * **Compiler Vectorization**: Analyzes auto-vectorization across scalar fallback vs. 256-bit AVX2 vector SIMD instructions.

### 6. [toolchain-linker-lab](https://github.com/Super-cod/toolchain-linker-lab) — Translation Units, Linking & ABI Laboratory
> **C++ Toolchains • Object Linking • Symbol Resolution • Name Mangling • Relocation Patching • DWARF**
* Hands-on laboratory dissecting the five core stages of native compilation and linking:
  * **Module 1 (Preprocessor & Translation Units)**: Header guards vs. `#pragma once`, macro token pasting, include order side-effects.
  * **Module 2 (Name Mangling & C++ ABI)**: Itanium C++ ABI type-encoding (`_Z3addii`), namespace mangling, and `extern "C"` linkage boundaries.
  * **Module 3 (Weak Symbols vs. ODR Violations)**: Strong vs. weak symbol overriding (`__attribute__((weak))`), multiple definition errors, and template deduplication.
  * **Module 4 (Relocations Inspection & Patching)**: Proves PC-relative displacement calculation ($\text{Displacement} = \text{Target} - (\text{CallAddr} + 5)$), replacing dummy object placeholders (`e8 00 00 00 00` $\to$ `e8 9f 00 00 00`).
  * **Module 5 (Debug Symbols & DWARF)**: Measures `-O2 -g` vs. `-O2 -s` binaries, proving DWARF `.debug_*` sections consume 90% disk footprint with zero runtime CPU overhead.

### 7. [bin-symbol-explorer](https://github.com/Super-cod/bin-symbol-explorer) — Binary Format & Symbol Table Inspector
> **Modern C++ • ELF64 & PE/COFF • Object Files • Relocation Records • Symbol Resolution**
* Structural parser and inspector for binary object files (`.o`, `.obj`) and relocatable executables.
* Inspects ELF64 headers, section header tables (`.text`, `.data`, `.bss`, `.rodata`), symbol tables (`.symtab`, `.strtab`), and relocation entries (`.rel`, `.rela`).
* Provides cross-platform structural parsing for Windows PE/COFF headers, sections, and export tables.
* Diagnoses symbol binding attributes (`STB_LOCAL`, `STB_GLOBAL`, `STB_WEAK`), symbol types (`STT_FUNC`, `STT_OBJECT`), and unreferenced externals.

---

## Skills & Core Competencies Matrix

| Engineering Discipline | Concrete Competencies & Technologies |
| :--- | :--- |
| **C++ Systems Programming** | **C++20**, modern RAII, rule of 5, move semantics, memory model, custom allocators, templates, cache line alignment (`alignas`), bit manipulation, zero-overhead abstractions |
| **Compiler Engineering** | Lexical analysis, recursive descent parsing, AST construction, symbol tables, lexical scoping, 3-Address Code (3AC) linear IR, SSA principles, Constant Folding, Constant Propagation, Dead Code Elimination (DCE), Code Generation |
| **PTX & GPU Computing** | **PTX Virtual ISA** (`.version 7.0`, `.target sm_75`), NVIDIA Driver API (`nvcuda.dll`), shared memory SRAM tiling (`bar.sync`), memory coalescing (128-byte transactions, `ld.global.v4.f32`), warp divergence serialization, thread block grid scheduling |
| **Binary Formats & Linkers** | **ELF64 & PE/COFF** parsing, section headers (`.text`, `.data`, `.bss`, `.rodata`), symbol binding (`STB_LOCAL`, `STB_GLOBAL`, `STB_WEAK`), relocation types, PC-relative displacement patching, Itanium C++ ABI mangling, DWARF debug symbols |
| **Computer Architecture** | CPUID instruction queries, L1/L2/L3 cache hierarchies, spatial/temporal cache locality, struct member alignment & padding, multi-core false sharing (MESI/MOESI invalidation), branch prediction & CMOV, AVX2 SIMD vectorization |
| **AI Systems & Inference** | Multi-Head Attention mechanisms, autoregressive decoding, stateful Key-Value (KV) caching, Vision Transformer (ViT) patch embedding, cross-modal linear projection, nucleus (top-$p$) sampling |
| **Toolchains & Testing** | GCC 14, Clang, MinGW-w64, CMake, Ninja, GNU Binutils (`readelf`, `objdump`, `nm`, `c++filt`), GDB, Python `ctypes`, PyTorch, PowerShell test automation |

---

## Verification & Build Philosophy

All featured repositories adhere to rigorous software engineering practices:
* **Zero Dependency Bloat**: Core systems and compiler modules are implemented in pure, modern C++ without bulky external frameworks.
* **Deterministic Test Automation**: Every project includes automated test scripts runnable in a single command, verifying mathematical invariants and error bounds.
* **Hardware-Grounded Empirical Metrics**: Performance claims are backed by reproducible benchmarks executed directly on physical silicon (Intel Core i7-12650H CPU and NVIDIA GeForce RTX 3050 Laptop GPU).

---

## Contact & Links

* **GitHub**: [@Super-cod](https://github.com/Super-cod)
* **Target Position**: NVIDIA Software Intern — PTX Compiler team
