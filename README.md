<div align="center">
    <p>Official implementation of the method described in:<br>
    <em>"VocalScape and MDemucs: A dataset of real-world audio scenarios and a multi-residual source separation model"</em></p>
</div>

<br>

---

## Overview

**MDemucs** is an efficient deep learning model specialized for separating human voices from environmental sounds in real-world acoustic scenarios, with design choices targeted at the unique challenges of soundscapes. The model originated from the need for robustness and effectiveness in the new VocalScape dataset, which systematically simulates diverse and challenging real audio scenes.

MDemucs leverages Soundloom, a flexible library for hierarchical dataset generation with constraint-based mixing. VocalScape, the dataset used for benchmarking, was created using Soundloom and fully available at [github.com/matcarollo/vocalscape](https://github.com/matcarollo/vocalscape). Soundloom itself is open source and documented at [github.com/matcarollo/soundloom](https://github.com/matcarollo/soundloom).

---

## Method

### Multi-Residual Architecture

MDemucs features a symmetric encoder–decoder structure with four levels, combining wide convolutional layers and multi-scale residual paths. The core innovation is the **Multi-Residual Block (MRB)**—parallel convolutional branches with different kernel sizes (3, 5, 7) that analyze time dependencies at multiple scales. Outputs are adaptively fused using a "Fusion Factory", employing techniques like Residual Gating and Multi-Residual Attention Convolution Fusions.

The model achieves state-of-the-art results on VocalScape using only 45.7M parameters—significantly less than many competitors—while maintaining high separation quality for both foreground (voice) and background (environmental) targets.

---

## Performance Highlights

MDemucs was rigorously compared with contemporary baselines, with all models trained from scratch under the same conditions on the VocalScape benchmark. Results are shown below:

| Model                  | SDR Environment | SDR Human Voices | Parameters (M) |
|------------------------|-----------------|------------------|----------------|
| Demucs (2019)          | 19.31           | 18.14            | 133.7          |
| HDemucs (2021)         | 20.05           | 18.85            | 83.6           |
| HTDemucs (2023)        | 18.57           | 17.28            | 26.8           |
| MossFormer (2023)      | 18.69           | 17.52            | 42.1           |
| MossFormer2 (2024)     | 20.37           | 19.26            | 55.7           |
| SepFormer (2022)       | 12.52           | 11.08            | 26.0           |
| SepReFormer (2025)     | 19.69           | 18.78            | 55.3           |
| Wave-U-Net (2018)      | 14.55           | 12.99            | 21.5           |
| **MDemucs (ours)**     | **21.03**       | **19.94**        | **45.7**       |


The evaluation demonstrates that MDemucs achieves superior sound separation with a markedly lower parameter count, setting a new benchmark for efficient and robust learning in unconstrained soundscape separation.

---

## Installation

```bash
git clone https://github.com/matcarollo]/MDemucs.git
cd MDemucs
pip install .
```

---

---

## License

This project is released under MIT Licence. The VocalScape dataset combines audio from Common Voice (CC0), ESC-50 (CC BY-NC), and UrbanSound8K (research-only license).

---

## Acknowledgments

Research led at the Neurone Lab, DISA-MIS, University of Salerno, and NAIR Research Centre, with support from Sonogram Technologies.
