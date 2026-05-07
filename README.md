# OPERA Reproduction Baseline

<div align="center">

![OPERA](https://img.shields.io/badge/OPERA-CVPR_2024-blue)
![Status](https://img.shields.io/badge/Status-Baseline_Ready-brightgreen)
![License](https://img.shields.io/badge/License-MIT-green)

**OPERA: Alleviating Hallucination in Multi-Modal Large Language Models via Over-Trust Penalty and Retrospection-Allocation**

[📄 Paper](https://arxiv.org/abs/2403.00321) • [🚀 Quick Start](#-quick-start) • [📖 Usage](#-usage)

</div>

---

## 📌 About This Repository

This is a **clean reproduction baseline** of the OPERA paper (CVPR 2024).

### What's Included

✅ **Original paper implementation**:
- Attention-based columnar pattern detection
- Over-trust penalty mechanism
- Retrospection-allocation re-decoding
- CHAIR / POPE evaluation scripts

### What's NOT Included

❌ **Removed**:
- OPTR improvement experiments
- Grid search parameter studies
- Mock/synthetic data generation
- Custom audit reports

> **For improved versions and parameter studies**, see: [OpTr Repository](https://github.com/poncioponcho/OpTr)

---

## 🚀 Quick Start

### Installation

```bash
# Clone repository
git clone https://github.com/shikiw/OPERA.git
cd OPERA

# Create conda environment
conda env create -f environment.yml
conda activate opera

# Install dependencies
pip install -r requirements.txt
```

### Model Setup

Download pretrained model weights:

| Model | Size | Source |
|-------|------|--------|
| MiniGPT-4 7B | ~14 GB | [ModelScope](https://modelscope.cn/models/Vision-CAIR/MiniGPT-4) |
| LLaVA-1.5-7B | ~14 GB | [HuggingFace](https://huggingface.co/liuhaotian/llava-v1.5-7b) |

```bash
mkdir -p checkpoints
# Place model weights in checkpoints/
```

### Run Inference & Evaluation

```bash
# Run OPERA with default parameters
python scripts/run_opera.py \
    --model-path checkpoints/pretrained_minigpt4.pth \
    --output-file output.jsonl

# Evaluate with CHAIR
python chair.py --cap_file output.jsonl
```

---

## 🔧 OPERA Parameters

| Parameter | Default | Range | Description |
|-----------|---------|-------|-------------|
| `threshold` | 15 | [5, 30] | Columnar pattern detection threshold |
| `num_attn_candidates` | 5 | [3, 10] | Number of attention candidates to check |
| `penalty_weights` | 1.0 | [0.0, 5.0] | Penalty strength for over-trust |
| `scale_factor` | 50 | [10, 100] | Scaling factor for attention intensity |

---

## 📊 Expected Results

Based on the original paper (MSCOCO val2014, 500 images):

| Method | CHAIR-s ↓ | CHAIR-i ↓ |
|--------|-----------|-----------|
| Baseline (no OPERA) | ~53% | ~21% |
| **OPERA (default)** | **~48%** | **~13.6%** |

---

## 📝 Citation

```bibtex
@inproceedings{opera2024,
  title={OPERA: Alleviating Hallucination in Multi-Modal Large Language Models via Over-Trust Penalty and Retrospection-Allocation},
  author={...},
  booktitle={CVPR},
  year={2024}
}
```

---

## 🔗 Related Resources

- **Paper**: [OPERA (CVPR 2024)](https://arxiv.org/abs/2403.00321)
- **Original Code**: [shikiw/OPERA](https://github.com/shikiw/OPERA)
- **Improvements**: [OpTr Repository](https://github.com/poncioponcho/OpTr)

---

<div align="center">

**Clean Baseline** | Ready for Reproduction

*Last updated: 2026-05-07*

</div>
