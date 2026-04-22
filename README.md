# Secure Local LLM Framework: Air-Gapped GRC Infrastructure

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Python](https://img.shields.io/badge/python-3.10%2B-blue) ![Status](https://img.shields.io/badge/Status-IEEE%20TechRxiv-orange)

## 📖 Overview
This repository provides the official open-source implementation of the **"Local-First" Governance, Risk, and Compliance (GRC) framework** for high-assurance environments.

Designed for sectors with strict data sovereignty requirements (Legal, Healthcare, Defense), this framework provides a secure, air-gapped execution environment to run Large Language Models (LLMs) locally, effectively neutralizing "Shadow AI" data leakage risks.

## 📝 Academic Reference
This implementation supports the research presented in: 
**"Mitigating Data Leakage in High-Compliance Environments: A Governance Framework for Local-LLM Adoption"**

*   **[Read the Full Paper on IEEE TechRxiv](https://doi.org/10.36227/techrxiv.176800912.24304866/v1)**

## 🛡️ Key Architectural Contributions
1. **Ephemeral Memory Decryption:** Implements a "Read-and-Forget" pipeline where sensitive context (PDFs, ASR streams) exists exclusively in volatile RAM, with active sanitization to prevent post-incident forensic recovery.
2. **Dynamic Hardware Abstraction Layer (HAL):** Decouples inference engines from the compiled binary. Performs a runtime 'Pre-Flight Audit' to dynamically inject hardware-specific dependencies (AVX2/CUDA), ensuring high performance on heterogeneous hardware.
3. **Compiler Hardening:** Utilizes a custom Nuitka build pipeline to transpile Python logic into native C++ machine code, enhancing resistance to reverse engineering and preventing bytecode exposure.
4. **Deterministic Command Routing:** Acts as a sandbox-level egress filter to prevent "Tool Hallucination," ensuring the AI cannot execute unauthorized external commands.

## ⚙️ Repository Structure
*   `ai_manager.py`: Orchestrates model inference and context management.
*   `engine_loader.py`: Implements the HAL for runtime dependency injection.
*   **`encryption_utils.py`**: Manages hardware-backed key storage via system-native credential vaults.
*   **`voice_manager.py`**: Handles zero-disk-footprint ASR (Automatic Speech Recognition).
*   **`build_pipeline.py`**: Reproducible Nuitka compilation script for "Commercial-Grade" deployment.

## 🚀 Deployment & Reproducibility
To replicate the research results on your local machine:

### 1. Environment Setup:
```bash
pip install -r requirements.txt
```
### 2. Inference Audit:
The framework detects hardware capabilities automatically. Run the benchmark to verify throughput:
```bash
python benchmark.py
```
### 3. Hardened Compilation:
To build the hardened standalone executable as described in the research paper:
```bash
python build_pipeline.py
```

### 🏢 Enterprise Licensing
The core framework is licensed under MIT for research and reproducibility. For enterprise-grade, Nuitka-hardened implementations (Cyphie Pro), please contact the author for commercial licensing.

### 📄 Research & Citation

This software is the official implementation of the GRC-focused "Local-First" architecture, If you use this framework in your research, please

**Cite as:**
> Jamil Alshaer. Mitigating Data Leakage in High-Compliance Environments: A Governance Framework for Local-LLM Adoption. TechRxiv. January 10, 2026. DOI: 10.36227/techrxiv.176800912

**BibTeX:**
```bibtex
@article{alshaer2026mitigating,
  title={Mitigating Data Leakage in High-Compliance Environments: A Governance Framework for Local-LLM Adoption},
  author={Alshaer, Jamil},
  journal={TechRxiv},
  publisher={IEEE},
  year={2026},
  month={jan},
  doi={10.36227/techrxiv.176800912}
}
