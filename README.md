# ECE6252_FunML_AI_Risk_Robustness

This repository contains the AI Risk final project for the Fall 2026 ECE-6252 FunML class.

## Project Overview

This project studies neural network robustness for traffic sign classification under challenging visual conditions. The experiments evaluate whether system-level safety mechanisms can improve model reliability under distribution shift.

## Dataset

Dataset: CURE-TSR (Traffic Sign Recognition)  
Link: https://ieee-dataport.org/open-access/cure-tsr-challenging-unreal-and-real-environments-traffic-sign-recognition

The dataset contains traffic sign images under different challenge types and challenge levels.

## Reproducibility

To reproduce the results, simply open the provided Jupyter notebooks and run all cells sequentially. 

Make sure the CURE-TSR dataset path is correctly set before execution. The experiments are fully implemented in the notebooks, and running them will automatically generate all reported metrics and results.

## Viewpoint A

Robustness does not always need to be explicitly communicated to users, as systems can improve safety internally through operating envelopes and uncertainty gating.

### Experiment Pipeline

1. Train a baseline ResNet-18 model for traffic sign classification.
2. Evaluate the baseline model on the full test set.
3. Apply an operating envelope by accepting only selected challenge levels.
4. Apply uncertainty gating by accepting predictions only when the model confidence is above a threshold.
5. Compare accuracy, coverage, risk, ECE, NLL, and Brier score.

### Files

- `Experiment_A.ipynb`: Main notebook for Viewpoint A experiments.

## Viewpoint B

Even with operating envelopes and uncertainty gating, robustness must still be explicitly communicated, because internal safety mechanisms cannot be fully trusted and deployers require real-world feedback to improve the model's robustness.

### Experiment Pipeline

1. Train a baseline ResNet-18 model using only Level 1–2 CURE-TSR images.
2. Test the baseline model on both Val Level 1–2 and severe OOD Level 4–5 data.
3. Train a second ResNet-18 model with Gaussian-noise augmentation.
4. Train a third ResNet-18 model with multi-corruption augmentation, including noise, blur, darkening, over-exposure, and haze.
5. Apply uncertainty gating to all three models using confidence-based rejection.
6. Compare performance under distribution shift using accuracy, accepted accuracy, coverage, risk, ECE, NLL, and Brier score.
7. Use the results to evaluate whether internal safety mechanisms are reliable enough, or whether robustness information must still be explicitly communicated to deployers.

## Setup Instructions
### Create and activate a Python environment:
```text
python -m venv venv
source venv/bin/activate      # Mac/Linux
venv\Scripts\activate         # Windows
pip install -r requirements.txt    # Install dependencies
```

## Repository Structure

```text
├── Experiment_A.ipynb
├── Experiment_B.ipynb
├── README.md
└── requirements.txt
```
