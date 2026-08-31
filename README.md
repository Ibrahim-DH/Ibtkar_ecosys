<div align="center">

# إبتكار | Ibtkar

### A Polyglot General Purpose Programming Language & Ecosystem

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22159851.svg)](https://zenodo.org/records/22159851)
[![Rust](https://img.shields.io/badge/Language-Rust%201.85+-orange.svg)](https://www.rust-lang.org/)
[![License](https://img.shields.io/badge/License-MIT%20%2F%20Commercial-blue.svg)](#license)

<p align="center">
  <b>Bilingual Syntax (Arabic RTL & English LTR)</b> • 
  <b>Dual-Execution (Tree-Walk & Native Rust Transpiler)</b> • 
  <b>MatnCode IDE & Custom Terminal</b>
</p>
    <img width="1911" height="922" alt="hero" src="https://github.com/user-attachments/assets/e9f273b9-0f42-4141-a0c8-cb8d19c27e1b" />
</div>

---


> ### Repository Status: LEAP 2026 Showcase & Phased Release
> The Ibtkar compiler codebase is currently under **private evaluation and technical briefing** for the **LEAP 2026 Technology Conference (Aug 31 – Sep 3, 2026)**.
> 
> * **Public Open-Source Unlock Date:** **September 2026**
> * **What will be unlocked:** Full compiler frontend (Lexer, Pratt Parser), AST, Tree-Walk Interpreter, Rust Transpiler backend, Standard Library, and CLI binaries under the **MIT License**.
> * **Live Inquiries:** For academic evaluation, thesis sponsorship, or institutional inquiries during LEAP, you contact can **Ibrahim Al Dhuhian** ibrah.dh01@gmail.com or refer to the [Research Monograph](https://zenodo.org/records/22159851).

---

## Key Highlights

* **Cognitive Ergonomics & Linguistic Parity:** Grounded in Cognitive Load Theory and the *Sapir-Whorf hypothesis*, Ibtkar provides native right-to-left (RTL) Arabic syntax alongside left-to-right (LTR) English syntax compiling down to an identical, Abstract Syntax Tree (AST).


* **Dual-Execution Architecture:**
  
  * **Tree-Walk Interpreter:** Immediate interactive execution for rapid prototyping, REPL, and debugging with contextual error diagnostics.
 
   
  * **Source-to-Source Rust Transpiler:** Compiles dynamic Ibtkar ASTs directly into strictly typed, memory-safe Rust source code, compiled via LLVM into native binary executables.
* **Zero-Cost C-ABI FFI:** Dynamic foreign function interface allowing high-performance orchestration of external C/C++ shared libraries (Raylib hardware-accelerated graphics).
* **MatnCode IDE & Custom Terminal:** A dedicated lightweight Tauri/Rust development environment featuring spatial DOM virtualization, a custom Language Server (LSP), and a **Lexical Token Isolation Algorithm** that natively resolves Unicode Bidirectional Algorithm (UBA) bracket reversal.

---

## Performance

Benchmarked on **Intel Core i7-13700H @ 2.40 GHz, 16GB RAM, Windows 11**:

| Benchmark Task | Baseline (Python 3.13) | Baseline (Golang 1.25) | Ibtkar (Transpiler) | Multiplier vs. Python |
| :--- | :---: | :---: | :---: | :---: |
| **Array Iteration (1M Items)** | `0.107 s` | `0.023 s` | **`0.00078 s`** | **137× Faster** (-99.3%) |
| **Fibonacci-30 Recursion** | `0.191 s` | `0.016 s` | **`0.042 s`** | **4.5× Faster** (-78.0%) |

| Benchmark Task | Industry standard (VScode) | Ibtkar ecosystem (Matn) | Performance comparison |
| :--- | :---: | :---: | :---: |
| **IDE Idle Memory (RAM)** | `896.2 MB` (VS Code) | **`60.1 MB`** (MatnCode) | **14.9× Lighter** (-93.3%) |
| **Terminal Stress (1M Lines)** | `1,832.6 MB` (VS Code) | **`89.7 MB`** (MatnCode) | **20.4× Lighter** (-95.1%) |

<p align="center">
<img width="1420" height="567" alt="chart" src="https://github.com/user-attachments/assets/3577a71f-1d94-4361-9a34-e160ac95b5d7" />
</p>

---

## Syntactic Parity

Ibtkar maintains strict semantic and structural isomorphism across both linguistic pipelines:

### English LTR Pipeline
```ibt
func calculate_tax(num price, num rate) : num {
    let total = price * (1.0 + (rate / 100));
    return total;
}

let bill = calculate_tax(100.0, 15.0);
print("Final Bill: " + bill.str);
```

### Arabic RTL Pipeline
```ib
عرف حساب_الضريبة(عدد السعر، عدد النسبة) : عدد {
    حول الإجمالي = السعر * (1.0 + (النسبة / 100))؛
    ارجع الإجمالي؛
}

حول الفاتورة = حساب_الضريبة(100.0، 15.0)؛
اطبع("الإجمالي النهائي: " + الفاتورة.نصوص)؛
```

---

## Overview

```
                         ┌────────────────────────────────────────┐
                         │          BILINGUAL SOURCE CODE         │
                         │    (.ib Arabic RTL | .ibt English LTR) │
                         └───────────────────┬────────────────────┘
                                             │
                                             ▼
                         ┌────────────────────────────────────────┐
                         │            BILINGUAL LEXER             │
                         │    (Thompson NFA ──► Hopcroft DFA)     │
                         └───────────────────┬────────────────────┘
                                             │
                                             ▼
                         ┌────────────────────────────────────────┐
                         │      HYBRID PRATT / RD PARSER          │
                         │     (Elevated Bitwise Precedence)      │
                         └───────────────────┬────────────────────┘
                                             │
                                             ▼
                         ┌────────────────────────────────────────┐
                         │       LANGUAGE-AGNOSTIC AST            │
                         └───────────┬────────────────┬───────────┘
                                     │                │
                   ┌─────────────────┘                └─────────────────┐
                   ▼                                                    ▼
    ┌───────────────────────────────┐                    ┌───────────────────────────────┐
    │     TREE-WALK INTERPRETER     │                    │     RUST SOURCE TRANSPILER    │
    │  • Interactive REPL & Debug   │                    │  • Escape Analysis            │
    │  • Linked Scope Environments  │                    │  • Stack Promotion (let mut)  │
    │  • Upward Signal Routing      │                    │  • Optimized Native LLVM Bin  │
    └───────────────────────────────┘                    └───────────────────────────────┘
```

---

## Case Study: Native Arabic Machine Learning & Web Hosting

To demonstrate production capability without external AI dependencies:
1. **Model from Scratch:** Implemented matrix operations, forward pass, and backpropagation in native Arabic syntax.
2. **MNIST Dataset Training:** Trained on 60,000 handwritten digits with zero memory degradation.
3. **Embedded HTTP Microservice:** Served prediction weights via Ibtkar's standard library web server, classifying browser-drawn digits in real time ($<2\text{ ms}$ latency).

<p align="center">
<img width="1653" height="872" alt="mnist" src="https://github.com/user-attachments/assets/4031f32e-6196-4fc1-9d26-e59d01699e8f" />
</p>

---

## Research & Documentation

The foundational theoretical and empirical research behind Ibtkar is detailed in the comprehensive research monograph:

> **Al Dhuhian, I. (2026).** *A Polyglot General Purpose Programming Language & Ecosystem (Version v1.0.0). Zenodo.*  [https://doi.org/10.5281/zenodo.22159851](https://doi.org/10.5281/zenodo.22159851)

### BibTeX Citation
```bibtex
@article{aldhuhian2026ibtkar,
  author    = {Ibrahim Al Dhuhian},
  title     = {A Polyglot General Purpose Programming Language & Ecosystem},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.22159851},
  url       = {https://doi.org/10.5281/zenodo.22159851}
}
```

---

## Author & Inquiries

**Ibrahim Al Dhuhian**  
*Lead Systems Architect & Researcher*  
Saudi Arabia  

* **GitHub:** [@Ibrahim-DH](https://github.com/Ibrahim-DH)
* **Preprint DOI:** [10.5281/zenodo.22159851](https://doi.org/10.5281/zenodo.22159851)
* **Direct Email:** [ibrah.dh01@gmail.com](mailto:ibrah.dh01@gmail.com)

*Inquiries: Connect via email, for academic research collaborations, M.Sc. thesis sponsorship, or institutional pilot briefings.*

---
## Rleases 
For `Windows` or `Linux` install the language (beta version) installer from [Here](https://github.com/Ibrahim-DH/Ibtkar_ecosys/releases/tag/beta).

---
## License

* **Ibtkar Compiler & Standard Library:** To be released under the [MIT License](LICENSE) in September 2026.
* **MatnCode IDE:** Proprietary / Commercial licensing for enterprise, team collaboration, and institutional site deployments.

<div align="center">
  <sub>Advancing Sovereign Systems Computing & Localized Accessibility for the Next Generation of Engineers.</sub>

</div>
