## S-TOON: Secure Token-Oriented Object Notation Framework

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Python](https://img.shields.io/badge/python-3.10%2B-blue) ![Status](https://img.shields.io/badge/Status-IEEE%20TechRxiv-orange)

**A Middleware Protocol to Neutralize "Delimiter Dissolution" Attacks in LLM Serialization.**

This repository contains the official implementation of the **S-TOON (Strict-TOON)** protocol. It addresses the critical security vulnerabilities introduced by the industry's shift from JSON to Token-Oriented Object Notation (TOON), specifically preventing "Structural Masquerading" attacks in Generative AI pipelines.

**Researcher & Developer:** Jamil Alshaer  
**Affiliation:** Independent Researcher (Azimuth Logic Research)

### 📥 Research Context
This code accompanies the paper: *"Structural Vulnerabilities in Token-Oriented Object Notation (TOON)"*.
**[Read the Full Paper on IEEE TechRxiv](https://doi.org/10.36227/techrxiv.176800912)**

---

### 🚀 Key Technical Contributions

1.  **Invisible Sentinel Injection (`stoon_protocol.py`):**
    *   Implements a middleware layer that wraps user input in `<|S_START|>` and `<|S_END|>` tokens.
    *   Restores deterministic boundaries to the "noisy" TOON format without sacrificing token efficiency.

2.  **Adaptive Chain-of-Thought Prompting:**
    *   Discovered that simple delimiters fail on "Smart" models (e.g., Qwen-7B).
    *   Implemented a recursive reasoning strategy ("Scan -> Mask -> Extract") that forces the Attention Mechanism to respect structural sentinels.

3.  **Comparative Vulnerability Analysis:**
    *   Provides the first empirical quantification of the "Delimiter Dissolution" threat across Edge and Cloud architectures.

### 🛠️ Developer Usage

1.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

2.  **Import the Middleware:**
    ```python
    from stoon_protocol import STOON_Middleware

    # Initialize Sanitizer
    middleware = STOON_Middleware()

    # Wrap User Input (Securely)
    safe_payload = middleware.construct_payload(user_input_string, access_level="user")
    ```

3.  **Run the Stress Test:**
    To reproduce the "100% Vulnerability" findings on your own GPU:
    ```bash
    # Test on Cloud Architecture (Qwen-7B)
    python run_experiment.py --model qwen --iterations 100
    ```

### ⚡ Performance Validation

We conducted a batch stress-test ($n=100$) on both Edge and Cloud architectures. The results demonstrate that S-TOON completely neutralizes the threat.

| Model Architecture | Standard TOON (Vulnerable) | S-TOON (Protected) |
| :--- | :---: | :---: |
| **TinyLlama-1.1B** (Edge) | 100.0% Failure | ✅ **0.0% (Secure)** |
| **Qwen2.5-7B** (Cloud) | 100.0% Failure | ✅ **0.0% (Secure)** |

*Verified on NVIDIA T4 GPU (Google Colab).*

### 📄 Research & Citation

This software is the official implementation of the research framework published on **IEEE TechRxiv**.

**Cite as:**
> Jamil Alshaer. *Structural Vulnerabilities in Token-Oriented Object Notation (TOON): Analysis of Delimiter Dissolution & the S-TOON Mitigation Protocol.* TechRxiv. January 12, 2026. DOI: 10.36227/techrxiv.176800912

**BibTeX:**
```bibtex
@article{alshaer2026toon,
  title={Structural Vulnerabilities in Token-Oriented Object Notation (TOON): Analysis of Delimiter Dissolution & the S-TOON Mitigation Protocol},
  author={Alshaer, Jamil},
  journal={TechRxiv},
  publisher={IEEE},
  year={2026},
  month={jan},
  doi={10.36227/techrxiv.176800912}
}
