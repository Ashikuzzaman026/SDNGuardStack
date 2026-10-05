# SDNGuardStack

An explainable ensemble learning framework for high-accuracy intrusion detection in Software-Defined Networks (SDN).

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white" />
  <img src="https://img.shields.io/badge/Domain-Cybersecurity-8A2BE2?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Explainability-SHAP-FF6F00?style=for-the-badge" />
</p>

## Overview

SDNGuardStack is a research-oriented intrusion detection framework for Software-Defined Networks (SDN). The project focuses on building an explainable and high-performing machine learning pipeline for detecting malicious traffic in SDN environments.

## Contributors

- Ashikuzzaman
- Mahabubur Rahman
- Md. Ahsan Arif
- Md. Manjur Ahmed
- Md. Mehedi Hasan

## Setup

### 1. Clone this repository

```bash
git clone https://github.com/Ashikuzzaman026/SDNGuardStack.git
cd SDNGuardStack
```

### 2. Create a virtual environment

#### Linux/macOS

```bash
python3 -m venv SDNGuardStackEnv
source SDNGuardStackEnv/bin/activate
```

#### Windows

```bash
python -m venv SDNGuardStackEnv
SDNGuardStackEnv\Scripts\activate
```

### 3. Install the dependencies

```bash
python -m pip install --upgrade pip
pip install numpy pandas scipy scikit-learn
pip install matplotlib seaborn jupyter
pip install imbalanced-learn shap
pip install sklearn-genetic
```

## Dataset

The project uses SDN network-flow data containing normal and malicious traffic.

The repository includes:

```text
InSDN_Dataset.zip
```

The experimental workflow uses traffic sources such as:

```text
metasploitable-2.csv
OVS.csv
Normal_data.csv
```

Extract the dataset archive before running the notebook.

## Dataset Classes

The dataset contains multiple traffic categories, including:

- Normal
- Probe
- DoS
- DDoS
- BFA
- BOTNET
- U2R
- Web-Attack

## Experimental Workflow

The project follows the following workflow:

```text
Dataset Loading
      |
      v
Data Integration
      |
      v
Data Cleaning and Validation
      |
      v
Feature Encoding
      |
      v
Label Encoding
      |
      v
Class Distribution Analysis
      |
      v
Under-sampling / Over-sampling
      |
      v
Feature Standardization
      |
      v
Statistical Feature Screening
      |
      v
Mutual Information Feature Selection
      |
      v
Ensemble Model Training
      |
      v
Performance Evaluation
      |
      v
SHAP-based Explainability
```

## Feature Processing

The preprocessing workflow includes:

- Loading and combining network-flow datasets
- Checking missing values
- Inspecting data types and class distributions
- Encoding flow identifiers
- Encoding source and destination IP addresses
- Encoding target labels
- Removing unnecessary columns
- Standardizing numerical features
- Removing statistically insignificant features
- Selecting informative features using Mutual Information

The processed features include network-flow attributes such as:

- Flow ID
- Source IP
- Destination IP
- Source Port
- Destination Port
- Protocol
- Flow Duration
- Packet-rate statistics
- Inter-arrival-time statistics
- Forward header length
- Backward header length
- Initial backward window size

## Class-Balancing Experiments

The project investigates class-balancing strategies to improve the detection of minority attack categories.

The notebook includes experiments involving:

- Under-sampling of majority classes
- Over-sampling of minority classes
- Comparison of different data distributions
- Evaluation of class-level detection performance

## Feature Selection

The project applies statistical and information-based feature-selection methods.

### Statistical Feature Screening

Analysis of variance is used to identify features that provide limited discriminatory information across traffic classes.

### Mutual Information

Mutual Information is used to rank features according to their relationship with the target label.

Feature selection helps reduce:

- Noise
- Redundant features
- Computational cost
- Model complexity
- Potential overfitting

## Ensemble Learning

SDNGuardStack uses an ensemble-learning approach for multi-class intrusion detection.

Multiple base learners are combined to produce the final prediction:

```text
Selected Network Features
          |
          +------------------+
          |                  |
          v                  v
    Base Learner 1     Base Learner 2
          |                  |
          +--------+---------+
                   |
                   v
        Ensemble Decision Layer
                   |
                   v
          Final Classification
```

The ensemble approach is intended to improve prediction stability, robustness, and generalization compared with a single classifier.

The complete implementation is available in:

```text
insdn_under+over.ipynb
```

## Explainability

The project uses SHAP (SHapley Additive exPlanations) to analyze model predictions.

The explainability analysis focuses on:

- Important features across the dataset
- Features contributing to malicious predictions
- Features supporting benign predictions
- Local explanations for individual traffic records
- Global interpretation of model behavior

This helps make the intrusion-detection process more transparent and useful for security analysis.

## Evaluation

The model is evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- Classification report
- Cohen's Kappa

Reported experimental results include:

```text
Accuracy:       99.98%
Cohen's Kappa:  0.9998
```

Results may vary depending on the dataset version, preprocessing configuration, sampling strategy, random seed, and software-library versions.

## Project Structure

```text
SDNGuardStack/
├── InSDN_Dataset.zip
├── insdn_under+over.ipynb
└── README.md
```

### File Description

| File | Description |
|---|---|
| `InSDN_Dataset.zip` | Dataset archive used for the experiments |
| `insdn_under+over.ipynb` | Main notebook containing preprocessing, feature selection, sampling, model training, evaluation, and SHAP analysis |
| `README.md` | Project documentation |

## Run the Project

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the following notebook:

```text
insdn_under+over.ipynb
```

Run the cells sequentially, beginning with dataset loading and preprocessing.

## Reproducibility

For reproducible experiments:

- Use a dedicated virtual environment.
- Keep the dataset files in the expected location.
- Run notebook cells in the correct order.
- Preserve the label-encoding mapping.
- Use fixed random seeds where applicable.
- Keep the same sampling configuration when comparing experiments.
- Avoid data leakage between training and testing data.
- Record the Python and package versions used.

## Research Publication

The project is associated with the following research publication:

> **SDNGuardStack: An Explainable Ensemble Learning Framework for High-Accuracy Intrusion Detection in Software-Defined Networks**

**Authors:** Ashikuzzaman, Mahabubur Rahman, Md. Ahsan Arif, Md. Manjur Ahmed, and Md. Mehedi Hasan

**Conference:** 2026 IEEE 15th International Conference on Communication Systems and Network Technologies (CSNT)

**Pages:** 638–643

**Publisher:** IEEE

**IEEE Xplore:**  
https://ieeexplore.ieee.org/document/11502458

## Citation

```bibtex
@inproceedings{ashikuzzaman2026sdnguardstack,
  author    = {Ashikuzzaman and
               Rahman, Mahabubur and
               Arif, Md. Ahsan and
               Ahmed, Md. Manjur and
               Hasan, Md. Mehedi},
  title     = {SDNGuardStack: An Explainable Ensemble Learning Framework for High-Accuracy Intrusion Detection in Software-Defined Networks},
  booktitle = {2026 IEEE 15th International Conference on Communication Systems and Network Technologies (CSNT)},
  pages     = {638--643},
  publisher = {IEEE},
  year      = {2026}
doi       = {10.1109/CSNT69054.2026.11502458}
}
```

## Future Work

- Real-time deployment in an SDN controller
- Online and incremental learning
- Zero-day attack detection
- Cross-dataset evaluation
- Automated hyperparameter optimization
- Adversarial robustness analysis
- Integration with Ryu, ONOS, or OpenDaylight
- Lightweight deployment for real-time traffic monitoring

## License

No open-source license is currently included in this repository.

Please contact the contributors before redistributing or reusing the implementation.
