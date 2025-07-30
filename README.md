# Hyperelastic TPMS Metamaterial Dataset

## Overview

This repository contains the first open-source, physically validated dataset of microscale hyperelastic metamaterials obtained by interpolating between eight TPMS primitives. The dataset comprises the results of 274 uniaxial compression experiments on unique 3D-printed microscale structures.

This data was collected for the paper:
**Data-Efficient Discovery of Hyperelastic TPMS Metamaterials with Extreme Energy Dissipation**
<https://doi.org/10.1145/3721238.3730759>

The dataset was generated with physical printing and testing, guided by a batch Bayesian optimization process to discover structures with exceptional energy dissipation capabilities.

## Dataset Structure

The dataset is organized into subdirectories within the main `data/` folder. Each subdirectory is named after the string representation of the structure's parameters and contains the data for a single experimental sample.

```
data/
├── [params_string_1]/
│   ├── [params_string_1].json
│   └── [params_string_1]_plot.png
│
├── [params_string_2]/
│   ├── [params_string_2].json
│   └── [params_string_2]_plot.png
...
```

-   `[params_string]`: A string representation of the 8 parameters defining the structure (e.g., `"0.1_0.2_0.0_0.1_0.0_0.4_0.2_0.0"`).
-   `.json` file: Contains the raw stress-strain data for the sample.
-   `.png` file: A plot visualizing the stress-strain curve for the corresponding sample.

## File Format

Each sample is stored in a `.json` file containing three keys: `params`, `strain`, and `stress`.

```json
{
  "params": [0.0, 0.0, 0.24, 0.2, 0.0, 0.56, 0.0, 0.0],
  "strain": [0.0, 0.005, ..., 0.595, 0.0],
  "stress": [0.0, 0.001, ..., 0.45, 0.01]
}
```

-   **`params`**: An 8-element array of floating-point numbers that sum to 1.0. These are the barycentric weights used to interpolate between the 8 TPMS primitives to define the structure's geometry. The order of primitives is:

  1. Schoen Gyroid
  2. Schwarz Diamond
  3. Schwarz P
  4. Schoen IWP
  5. Neovius
  6. Fischer-Koch
  7. Schoen FRD
  8. PMY

-   **`strain`**: A 120-element array representing the engineering strain applied during the compression test. The curve includes both the loading (increasing strain) and unloading (decreasing strain) phases.

-   **`stress`**: A 120-element array representing the corresponding engineering stress (in Megapascals, MPa) measured during the test.

## Data Generation

Each structure was fabricated from a hyperelastic photosensitive resin (IP-PDMS) using two-photon lithography (Nanoscribe Professional GT2). The resulting micro-lattices (approx. 170x170x94 µm) were uniaxially compressed using a nanoindenter with a flat-punch tip to measure the force-displacement response, which was then converted to a stress-strain curve.

## Citation

If you use this dataset in your research, please cite our paper:

```bibtex
@inproceedings{perroni-scharf2025data,
  author = {Perroni-Scharf, Maxine and Ferguson, Zachary and Butruille, Thomas and Portela, Carlos M. and Konakovi\'{c} Lukovi\'{c}, Mina},
  title = {Data-Efficient Discovery of Hyperelastic TPMS Metamaterials with Extreme Energy Dissipation},
  year = {2025},
  isbn = {979-8-4007-1540-2},
  publisher = {Association for Computing Machinery},
  address = {New York, NY, USA},
  url = {[https://doi.org/10.1145/3721238.3730759](https://doi.org/10.1145/3721238.3730759)},
  doi = {10.1145/3721238.3730759},
  booktitle = {Special Interest Group on Computer Graphics and Interactive Techniques Conference Conference Papers},
  series = {SIGGRAPH '25}
}
