## Secure Local LLM Framework: Air-Gapped GRC Infrastructure

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Python](https://img.shields.io/badge/python-3.10%2B-blue) ![Status](https://img.shields.io/badge/Status-IEEE%20TechRxiv-orange)

**The official open-source implementation of the "Local-First" Governance, Risk, and Compliance (GRC) framework for high-assurance environments.**

This repository contains the core infrastructure for a secure, air-gapped execution environment designed to reconcile strict data sovereignty with the utility of Generative AI. It allows organizations in high-compliance sectors (Legal, Healthcare, Defense) to utilize LLMs without the "Shadow AI" risks associated with cloud-based APIs.

**Researcher & Developer:** Jamil Alshaer  
**Affiliation:** Independent Researcher (Azimuth Logic Research)

### 📥 Research Context
This implementation accompanies the IEEE TechRxiv publication: *"Mitigating Data Leakage in High-Compliance Environments: A Governance Framework for Local-LLM Adoption."*.
**[Read the Full Paper on IEEE TechRxiv](https://doi.org/10.36227/techrxiv.176800912.24304866/v1)**

---

### 🚀 Key Technical Contributions

1.  **Ephemeral Memory Decryption:**
    *   Implements a "Read-and-Forget" ingestion pipeline. All sensitive data (PDF context, voice PCM buffers) is staged exclusively in volatile RAM.
    *   Features active RAM sanitization via Python garbage collection (gc.collect()) to ensure no forensic artifacts persist post-inference.

2.  **Dynamic Hardware Abstraction Layer (HAL):**
    *   Solves "DLL Hell" by decoupling inference backends from the compiled binary.
    *   Performs a runtime 'Pre-Flight Audit' to dynamically inject hardware-specific dependencies (AVX2/CUDA), allowing a single executable to run efficiently across heterogeneous hardware.

3.  **Compiler Hardening & Binary Obfuscation:**
    *   Utilizes a surgical Nuitka build pipeline to transpile Python logic into native C++ machine code, eliminating .pyc bytecode and preventing trivial reverse-engineering.

### 🏢 Enterprise Licensing
The core framework is licensed under MIT for research and reproducibility. For enterprise-grade, Nuitka-hardened implementations (Cyphie Pro), please contact the author for commercial licensing.

### 📄 Research & Citation

This software is the official implementation of the GRC-focused "Local-First" architecture.

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
