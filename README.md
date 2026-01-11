## Secure Local LLM Framework

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Python](https://img.shields.io/badge/python-3.10%2B-blue)

**A Local-First, Memory-Safe Inference Architecture for High-Compliance Environments.**

This repository contains the open-source backend framework used in **Cyphie**, a Governance tool for Shadow AI. It addresses the challenges of deploying secure, offline Large Language Models (LLMs) in environments requiring strict data sovereignty.

**Researcher & Developer:** Jamil Alshaer  
**Affiliation:** Independent Researcher (Azimuth Logic Research)

### 📥 Download the App
To see this framework in action with the full UI and animation engine, download the compiled commercial build:                       
**[Download Cyphie (Evaluation Edition)](https://azimuth-logic-research.itch.io/cyphie-secure-local-ai)**

---

### 🚀 Key Technical Contributions

1.  **Dynamic Hardware Abstraction (`engine_loader.py`):**
    *   Performs a "Pre-Flight Audit" of the host CPU/GPU.
    *   Dynamically injects AVX2 or CUDA dependencies into the runtime *after* Nuitka compilation.

2.  **Ephemeral Memory Staging (`voice_manager.py`):**
    *   Implements a RAM-only buffer for voice and document ingestion.
    *   Ensures sensitive data is streamed to inference without disk serialization (Anti-Forensics).

3.  **Self-Healing Encryption (`encryption_utils.py`):**
    *   Migrates legacy flat-file keys to the OS System Vault upon startup.

### 🛠️ Developer Usage

1.  Install dependencies: pip install -r requirements.txt
2.  Download a `tinyllama.gguf` model to the root folder.
3.  Run the reference GUI:
    ```bash
    python gui_demo.py
    ```
### ⚡ Performance Validation

This framework is optimized for speed on commodity hardware. You can verify the CPU inference performance on your own machine using the included benchmark script. This script uses a streaming token methodology to isolate generation latency.

```bash
benchmark.py
```   
## 📄 Research & Citation

This software is the official implementation of the research framework published on **IEEE TechRxiv**.

**Cite as:**
> Jamil Alshaer. *Mitigating Data Leakage in High-Compliance Environments: A Governance Framework for Local-LLM Adoption.* TechRxiv. January 10, 2026. DOI: [10.36227/techrxiv.176800912.24304866/v1](https://doi.org/10.36227/techrxiv.176800912.24304866/v1)

**BibTeX:**
```bibtex
@article{alshaer2026mitigating,
  title={Mitigating Data Leakage in High-Compliance Environments: A Governance Framework for Local-LLM Adoption},
  author={Alshaer, Jamil},
  journal={TechRxiv},
  publisher={IEEE},
  year={2026},
  month={jan},
  doi={10.36227/techrxiv.176800912.24304866/v1},
  url={https://doi.org/10.36227/techrxiv.176800912.24304866/v1}
}
