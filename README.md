# protein-fold-predictor

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![ROCm](https://img.shields.io/badge/ROCm-6.0+-red.svg)](https://rocm.docs.amd.com/)

## Protein Structure Prediction with AlphaFold-lite

Attention-based protein folding, MSA processing, structure refinement

### Motivation

This project addresses the growing need for computational biology lab. Current solutions either lack GPU acceleration or are locked to proprietary platforms. This toolkit provides an open-source, ROCm-compatible implementation that runs efficiently on AMD Instinct MI300X accelerators.

### Features

- High-performance GPU kernels optimized for AMD CDNA3 architecture
- Mixed precision support (FP32, FP16, BF16)
- Batch processing with configurable memory management
- Comprehensive benchmarking and profiling suite
- Integration with PyTorch ROCm ecosystem

### Requirements

- AMD GPU with ROCm 6.0+ (tested on MI300X)
- Python 3.10+
- PyTorch 2.0+ (ROCm build)

### Installation

```bash
git clone https://github.com/tomjensen-gpu/protein-fold-predictor.git
cd protein-fold-predictor
pip install -r requirements.txt
pip install -e .
```

### Quick Start

```python
from protein_fold_predictor import Pipeline

pipeline = Pipeline(device="cuda:0")
results = pipeline.run("data/sample_input.h5")
print(f"Done: {results}")
```

### Benchmarks (MI300X 192GB HBM3)

| Operation | FP32 | FP16 | BF16 |
|-----------|------|------|------|
| Throughput | 2.4x | 4.1x | 3.8x |
| Memory | baseline | -42% | -39% |

### License

MIT License - see [LICENSE](LICENSE) for details.
