# Hi, I'm Swayam Kapoor 👋

**Systems · Compilers · GPU Computing · Machine Learning**

I build things close to the metal and close to the model: a compiler that emits NVIDIA PTX, hand-written GPU kernels profiled on real hardware, and transformers and vision-language models implemented from scratch in PyTorch.

[![GitHub](https://img.shields.io/badge/GitHub-Super--cod-181717?style=flat&logo=github)](https://github.com/Super-cod)
[![Email](https://img.shields.io/badge/Email-swayamk139%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:swayamk139@gmail.com)

Open to internships and entry-level roles in systems, compilers, GPU and ML engineering.

---

## Featured projects

### [ptx-toy-compiler](https://github.com/Super-cod/ptx-toy-compiler)
`C++20` `Compilers` `IR` `PTX`

An educational compiler written in modern C++: recursive-descent parser, typed AST, three-address-code IR, optimization passes (constant folding, dead code elimination) and a backend that generates NVIDIA PTX. 12 passing tests.

### [cuda-kernel-perf-lab](https://github.com/Super-cod/cuda-kernel-perf-lab)
`PTX` `CUDA Driver API` `Python` `GPU performance`

Hand-written PTX kernels loaded through the CUDA Driver API and measured on an RTX 3050 laptop GPU. Covers memory coalescing, shared-memory tiling for GEMM and warp divergence, with results checked against CPU references. Measured: strided vs coalesced copy about **11x**, divergent vs uniform warps about **2x**, tiled vs naive GEMM about **1.4x**, against a cuBLAS reference about 4x faster than the tiled kernel.

### [Multimodal Vision-Language Model from scratch](https://github.com/Super-cod/Multimodal-Vision-Language-Model-from-scratch-in-PyTorch)
`PyTorch` `ViT` `Multimodal`

A PaliGemma/LLaVA-style VLM built without high-level model wrappers: ViT patch encoder, cross-modal projector and a causal decoder, with shape and gradient-flow tests.

### [Building_transformer_PyTorch](https://github.com/Super-cod/Building_transformer_PyTorch)
`PyTorch` `Transformers` `KV-cache`

A decoder-only transformer with a stateful KV-cache for fast autoregressive inference, plus tests for causal-mask correctness and cache equivalence.

### [PJT-Deep-Learning-Based-Real-Time-Multi-Camera](https://github.com/Super-cod/PJT-Deep-Learning-Based-Real-Time-Multi-Camera)
`Python` `FastAPI` `Swift / ARKit` `Computer vision`

Real-time multi-camera human localization: iPhones track people in 3D with ARKit and LiDAR, and a Python hub fuses them into one shared world frame for a live 3D web view.

### [ai-code-reviewer](https://github.com/Super-cod/ai-code-reviewer)
`FastAPI` `SQLAlchemy` `Gemini API` `GitHub OAuth`

A web app that pulls a GitHub pull request, indexes the code and produces a structured AI review (bugs, security, performance) that can be posted back as a PR comment.

---

## Systems labs

Small, dependency-free C++20 labs with measured results:

| Repo | What it shows |
| :--- | :--- |
| [cpp-arch-perf-lab](https://github.com/Super-cod/cpp-arch-perf-lab) | Cache locality (row- vs column-major, **7.4x**), struct padding (**1.6x**), AVX2/FMA SIMD, cache coherence, branch prediction, CPUID introspection |
| [toolchain-linker-lab](https://github.com/Super-cod/toolchain-linker-lab) | Preprocess/compile/assemble/link stages, symbol resolution, linker errors, relocations, DWARF debug info |
| [bin-symbol-explorer](https://github.com/Super-cod/bin-symbol-explorer) | ELF64 and PE/COFF inspector: headers, sections, symbols, relocations |

---

## More work

| Area | Projects |
| :--- | :--- |
| **Deep learning / vision** | [Swin-Transformers](https://github.com/Super-cod/Swin-Transformers) · [VISiOn_transformer](https://github.com/Super-cod/VISiOn_transformer) · [PLANT_DISEASE_BASED_DL_MODEL](https://github.com/Super-cod/PLANT_DISEASE_BASED_DL_MODEL) · [posture_detection_system_ai_project](https://github.com/Super-cod/posture_detection_system_ai_project) · [Drone_tracking](https://github.com/Super-cod/Drone_tracking) (YOLOv8) · [HCI_gaze](https://github.com/Super-cod/HCI_gaze) (gaze-motor stroke-rehab assessment prototype) |
| **Applied ML** | [Fraud_Blockchain_transaction](https://github.com/Super-cod/Fraud_Blockchain_transaction) (permissioned blockchain + fraud engine) · [Heart_guard](https://github.com/Super-cod/Heart_guard) · [reinforcement_snake_game](https://github.com/Super-cod/reinforcement_snake_game) |
| **Full-stack / apps** | [SuperJoin](https://github.com/Super-cod/SuperJoin) (evidence-grounded fact extraction over PDFs) · [dynamic-island](https://github.com/Super-cod/dynamic-island) · [TrackTempML-Live-Weather-Forecast](https://github.com/Super-cod/TrackTempML-Live-Weather-Forecast) |

---

## Tech stack

![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA%20%2F%20PTX-76B900?style=flat&logo=nvidia&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![C#](https://img.shields.io/badge/C%23-512BD4?style=flat&logo=dotnet&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

- **Systems & compilers:** C++20, lexing/parsing, IR design, optimization passes, code generation
- **GPU:** PTX, CUDA Driver API, memory hierarchy, kernel benchmarking
- **ML:** PyTorch, transformers, ViT, multimodal models, computer vision, scikit-learn
- **Backend & tooling:** FastAPI, SQLAlchemy, REST, WebSockets, CMake, PowerShell

---

## Get in touch

📫 [swayamk139@gmail.com](mailto:swayamk139@gmail.com) · 💻 [github.com/Super-cod](https://github.com/Super-cod)
