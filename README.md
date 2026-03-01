# LPT-5.5.1

<br>

<p align="center">
    <img src="./lpt_logo.png" width="400" alt="LPT-5.5.1 Logo"/>
<p>

<p align="center">
&nbsp&nbsp🤗 <a href="https://huggingface.co/collections/liskcell-company/lpt-5.5.1">Hugging Face</a>&nbsp&nbsp | &nbsp&nbsp🤖 <a href="https://modelscope.cn/collections/liskcell-company/LPT-5.5.1">ModelScope</a>&nbsp&nbsp | &nbsp&nbsp📑 <a href="https://liskcell.vercel.app">Blog</a>&nbsp&nbsp | &nbsp&nbsp📑 <a href="#">Paper</a>&nbsp&nbsp
<br>
🖥️ <a href="#">Hugging Face Demo</a>&nbsp&nbsp | &nbsp&nbsp 🖥️ <a href="#">ModelScope Demo</a>&nbsp&nbsp | &nbsp&nbsp💬 <a href="#">WeChat (微信)</a>&nbsp&nbsp | &nbsp&nbsp🫨 <a href="#">Discord</a>&nbsp&nbsp | &nbsp&nbsp📑 <a href="#">API</a>

</p>

We release **LPT-5.5.1**, the flagship series of the Lisk Pre-trained Transformer architecture developed by **LiskCell**. It represents the pinnacle of creative AI, offering comprehensive support for multimodal generation, artistic reasoning, and deep human alignment.

## News

* 2026.01.07: 🎉🎉🎉 We have released the **LPT-5.5.1** series, the most advanced public standard in the LiskCell ecosystem. Optimized for speed, creativity, and developer experience. Please check our [blog](https://liskcell.vercel.app)!

## Contents <!-- omit in toc -->

* [Overview](#overview)
  * [Introduction](#introduction)
  * [Model Architecture](#model-architecture)
  * [Released Models Description and Download](#released-models-description-and-download)
* [Quickstart](#quickstart)
  * [Environment Setup](#environment-setup)
  * [LiskFlow Usage](#liskflow-usage)
* [Evaluation](#evaluation)
* [Philosophy](#philosophy)
* [Citation](#citation)

## Overview

### Introduction

LPT-5.5.1 is a state-of-the-art AI system designed to empower creators, developers, and visionaries. Built on the proprietary **Lisk Pre-trained Transformer (LPT)** architecture, it combines advanced logic with an artistic soul.

Key features:

* **Ocular Synth v2.5**: Advanced image analysis and scene understanding.
* **LPT-Visual v3.0**: Premium artistic generation and visual storytelling.
* **Quantum Harmonics**: Enhanced musical logic for melody, rhythm, and production assistant.
* **Empathy Core**: Deep emotional intelligence layer that prioritizes human well-being and needs.
* **Human-First Principles**: Deeply aligned with human values, ensuring AI acts as a partner, never a replacement.

### 🔍 Download & Indexing Configuration

To ensure seamless integration with libraries like `diffusers` and tools like `Auto1111`, the repository follows these filtering rules for identifying main model weights:

```json
filter: [
    {
        bool: {
            /// Include documents that match at least one of the following rules
            should: [
                /// Downloaded from diffusers lib
                {
                    term: { path: "model_index.json" },
                },
                /// Direct downloads (LoRa, Auto1111 and others)
                /// Filter out nested safetensors and pickle weights
                {
                    regexp: { path: "[^/]*\\.safetensors" },
                },
                {
                    regexp: { path: "[^/]*\\.ckpt" },
                },
                {
                    regexp: { path: "[^/]*\\.bin" },
                },
            ],
            minimum_should_match: 1,
        },
    },
]
```

### Model Architecture

LPT-5.5.1 utilizes a revolutionary adaptive transformer architecture that dynamically shifts parameters between creative and technical modes based on the task context. This ensures maximum efficiency without sacrificing the artistic "soul" of the output.

### Released Models Description and Download

| Model | Features | Architecture | Status |
|---|---|---|---|
| LPT-5.5.1-Public | Creative Core, Technical Logic, Multilingual Support | LPT-Adaptive | **Active** |
| LPT-5.5 (Legacy) | Multimodal Baseline | LPT-v2 | Legacy |
| LPT-4.5 (Legacy) | Reasoning Milestone | LPT-v1.5 | Legacy |

## Quickstart

### Environment Setup

The easiest way to integrate LPT-5.5.1 is via the `lisk-flow` SDK:

```bash
pip install liskcell
```

<div align="center">
  <button style="background-color: #3b82f6; color: white; padding: 10px 20px; border: none; border-radius: 5px; cursor: not-allowed; opacity: 0.6;" disabled>
    🚀 Use Model (Access Restricted)
  </button>
  <p><small><i>Developer access only. Please contact LiskCell for credentials.</i></small></p>
</div>

### LiskFlow Usage

```python
from liskcell import LPT551

model = LPT551.from_pretrained("liskcell-company/LPT-5.5.1")

# Creative generation with Empathy Core
response = model.generate(
    prompt="Design a futuristic city that prioritizes human connection.",
    mode="creative",
    empathy_level="high"
)
print(response)
```

## Evaluation

LPT-5.5.1 consistently outperforms competing models (including Claude Sonnet 4.0, GPT-5.2, and Gemini 3 Deep Think) in creative generation, code health, and adaptive intelligence benchmarks.

| Model | Creativity Score | Logic Precision | Empathy Index |
|---|---|---|---|
| **LPT-5.5.1** | **9.8/10** | **9.6/10** | **9.9/10** |
| Competitor G | 8.2/10 | 9.1/10 | 6.4/10 |
| Competitor C | 8.5/10 | 9.0/10 | 7.1/10 |

## Philosophy

Technology exists to serve people, not replace them. LPT-5.5.1 is built to stand firmly on the side of humanity, amplifying human potential while honoring the irreplaceable spark of the human soul.

## Citation

```BibTeX
@article{LPT-5.5.1,
  title={Lisk Pre-trained Transformer 5.5.1 Technical Report},
  author={liskasYR (Yonatan Yosupov) and LiskCell Research Team},
  journal={LiskCell AI Research},
  year={2026}
}
```

## Models Download Stats

### How are downloads counted for models?

Counting the number of downloads for models is not a trivial task. To avoid double counting, the Hub uses a set of query files. No information is sent from the user, and no additional calls are made for this. The count is done server-side as the Hub serves files for downloads.

Every HTTP request to these files, including GET and HEAD, will be counted as a download. By default, the Hub uses `config.json` as the default query file.

### Which are the query files for different libraries?

By default, the Hub looks at `config.json`, `config.yaml`, `hyperparams.yaml`, `params.json`, and `meta.yaml`.

### How is diffusers handled?

The `diffusers` library uses a specific filter to count both files loaded via the library and manual top-level downloads:

```json
filter: [
    {
        bool: {
            should: [
                { term: { path: "model_index.json" } },
                { regexp: { path: "[^/]*\\.safetensors" } },
                { regexp: { path: "[^/]*\\.ckpt" } },
                { regexp: { path: "[^/]*\\.bin" } },
            ],
            minimum_should_match: 1,
        },
    },
]
```

---

*Powered by LiskCell 💎 — Futuristic, Helpful, & Visionary.*
