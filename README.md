# OpenPQD-Synthetic-Power-Quality-Dataset-Analysis-Toolkit-for-ML
An open-source dataset of synthetic power quality disturbances (PQD), ideal for training and validating machine learning models. Signals are generated using established mathematical models from scientific literature, with parameter ranges conforming to the IEEE 1159 standard. Includes a Python analysis framework for statistical exploration.

# OpenPQD: Synthetic Power Quality Dataset & Analysis Toolkit for ML

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

This repository provides a comprehensive, open-source dataset of 31 types of synthetic power quality disturbances (PQD), ideal for training and validating machine learning models. Signals are generated using established mathematical models, with parameter ranges conforming to the **IEEE 1159 standard**.

The project includes a modular Python analysis framework in a Jupyter Notebook for advanced statistical exploration, featuring correlation analysis and t-SNE visualizations to assess class separability.

## 📚 Dataset Overview

The dataset is generated using a programmatic approach based on a `PQDBaseGenerator` class, which provides a foundation for creating clean sine waves with randomized base parameters and noise. Each disturbance is then created by a dedicated generator class that applies a specific mathematical model.

The dataset contains **31 distinct classes** of power quality signals, separated into two main categories:

#### Individual Disturbances (11 Classes)
These are single, isolated power quality events:
1. Operational Signal (C1)
2. Sag (C2)
3. Swell (C3)
4. Interruption (C4)
5. Impulsive Transient (C5)
6. Oscillatory Transient (C6)
7. Flicker (C7)
8. Notch (C8)
9. Harmonics (C9)
10. Interharmonics (C10)
11. DC Offset (C11)

#### Mixed Disturbances (20 Classes)
These signals are complex waveforms created by combining two or more individual disturbances, providing a challenging dataset for advanced classification tasks:
12. Harmonics with Sag (M1)
13. Harmonics with Swell (M2)
14. Flicker with Sag (M3)
15. Flicker with Swell (M4) 
16. Sag with Oscillatory Transient (M5) 
17. Swell with Oscillatory Transient (M6)
18. Sag with harmonics (M7) 
19. Swell with harmonics (M8)
20. Harmonics with sag with flicker (M9)
21. Harmonics with swell with flicker (M10)
22. Sag with harmonics with flicker (M11)
23. Swell with harmonics with flicker (M12)
24. Sag with harmonics with Oscillatory Transient (M13)
25. Swell with harmonics with Oscillatory Transient (M14)
26. Harmonics with sag with Oscillatory Transient (M15)
27. Harmonics with swell with Oscillatory Transient (M16)
28. Harmonics with sag with flicker with Oscillatory Transient (M17)
29. Harmonics with swell with flicker with Oscillatory Transient (M18)
30. Sag with harmonics with flicker with oscillatory transient (M19)
31. Swell with harmonics with flicker with oscillatory transient (M20)

## ✨ Key Features

* **IEEE 1159 Compliant**: Disturbance parameters are randomized within standard-compliant ranges.
* **Modular Analysis**: The Jupyter Notebook is structured into independent **Global**, **Individual**, and **Mixed** analysis sections, which can be run without dependencies on each other.
* **Unified Parameter Framework**: A core feature of the analysis is the `unify_data` function, which transforms diverse disturbance parameters into a consistent set (`disturbance_magnitude`, `disturbance_duration`) for direct comparison.
* **Advanced Visualizations**:
    * **Correlation Heatmaps**: To analyze the statistical independence of generated parameters.
    * **3D t-SNE Plots**: To visualize the separability of disturbance classes in a reduced-dimensional space. The global analysis plot uses distinct markers (`●` for individual, `■` for mixed) to highlight group clustering.

##  Methodological Approach

A unique aspect of this framework is the handling of duration for steady-state disturbances (like Harmonics, Flicker). Since these events don't have a natural "duration," we use other probabilistically independent parameters as proxies (`flicker_frequency`, `mean of harmonic_phases`, etc.). This innovative approach allows for consistent six-parameter analysis across all signal types, which is particularly useful for testing the Monte Carlo simulation via the correlation matrix.

## 📂 Repository Structure

```
.
├── 📜 README.md
├── 📄 LICENSE
├── 🐍 requirements.txt
│
├── 📂 dataset/
│   └── 🔗 download_dataset.txt  (Link to the full HDF5 dataset on Google Drive)
│
├── 📂 analysis_notebook/
│   └── 📊 PQD_Analysis.ipynb      (The complete, modular Jupyter Notebook)
│
└── 📂 results_preview/
    └── (A sample of generated plots for a quick overview)
```

## 🚀 Getting Started

### 1. Prerequisites
This project requires Python 3 and the libraries listed in the `requirements.txt` file.

### 2. Download the Dataset
The full dataset is hosted externally to keep the repository lightweight. The public download link is available in `dataset/download_dataset.txt`. Please download the `PQD_Synthetic_Dataset` folder and place it in a location accessible by the notebook (e.g., the root of your Google Drive).

### 3. Run the Analysis
All analysis code is in `analysis_notebook/PQD_Analysis.ipynb`. It is designed to be run in an environment like Google Colab.

1.  **Run Section 1 (Master Setup & Core Functions)**: Execute the first two blocks (`Block 1: Master Configuration` and `Block 2: Master Functions`) once per session. This will load all configurations and define the necessary functions.
2.  **Choose Your Analysis**: Go to **Section 2 (Analysis Execution)** and run **only one** of the three execution blocks based on your needs:
    * `Run GLOBAL Analysis`
    * `Run INDIVIDUAL Analysis`
    * `Run MIXED Analysis`

## ✍️ Author & Citation

* **Author**: Leonardo Corral Trigueros

* **Citation**: If you use this dataset or framework in your research, please cite it using the following BibTeX entry. You will need to replace the URL and commit hash with your repository's specific details.

    ```bibtex
    @misc{CorralTrigueros2025,
      author = {Corral Trigueros, Leonardo},
      title = {OpenPQD: Synthetic Power Quality Dataset & Analysis Toolkit for ML},
      year = {2025},
      publisher = {GitHub},
      journal = {GitHub repository},
      howpublished = {\url{[[https://github.com/YOUR_USERNAME/YOUR_REPO_NAME](https://github.com/LeonardoCorral04/OpenPQD-Synthetic-Power-Quality-Dataset-Analysis-Toolkit-for-ML)]([https://github.com/YOUR_USERNAME/YOUR_REPO_NAME](https://github.com/LeonardoCorral04/OpenPQD-Synthetic-Power-Quality-Dataset-Analysis-Toolkit-for-ML))}},
      commit = {c8f9cecf3169aa8e7dffb3c6bc4e10cc7a111826}
    }
    ```

## ⚖️ License

This project is licensed under the GNU General Public License v3.0. See the `LICENSE` file for full details.
