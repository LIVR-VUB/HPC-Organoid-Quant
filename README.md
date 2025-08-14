[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff)](#) [![Matplotlib](https://custom-icon-badges.demolab.com/badge/Matplotlib-71D291?logo=matplotlib&logoColor=fff)](#) [![NumPy](https://img.shields.io/badge/NumPy-4DABCF?logo=numpy&logoColor=fff)](#) [![Scikit-learn](https://img.shields.io/badge/-scikit--learn-%23F7931E?logo=scikit-learn&logoColor=white)](#) [![CUDA](https://img.shields.io/badge/CUDA-76B900?logo=nvidia&logoColor=fff)](#) [![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=fff)](#)

# HPC-Organoid-Quant


# Organoid Detection and GFP Quantification

This project provides a complete and modular pipeline to detect organoids from **brightfield microscopy images**, with optional quantification of **GFP-positive regions** from corresponding fluorescence images.

### Features

- Works with **brightfield-only** images or **brightfield + GFP**
- Detects **irregular and fragmented organoids** as a **single object**
- Computes key morphological features:
  - Area
  - Centroid
  - Perimeter
  - Circularity
- If GFP is provided:
  - Quantifies GFP+ area
  - Calculates mean and total GFP intensity
- Generates annotated overlay images for visualization


#### More info on the features: https://github.com/arka2696/HPC-Organoid-Quant/blob/main/FeatureExplanation.md

## Project Structure

#### Input folder structure:
```
Organised_files/
└── B16 Spheroid_10% FBS/
    └── B16_control/
        └── B16 day 3/
            ├── BRIGHTFIELD_16173.jpg
            ├── BRIGHTFIELD_16174.jpg
            └── ...
````

#### Output folder structure:
```
OUTPUT/
├── B16 Spheroid_10% FBS/
│   └── B16_control/
│       └── B16 day 3/
│           ├── masks/
│           │   ├── mask_16173.png
│           │   └── ...
│           └── overlays/
│               ├── overlay_16173.png
│               └── ...
│
└── organoid_gfp_analysis.csv   ← all image results combined here
```
---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Organoid_GFP_Analysis.git
cd Organoid_GFP_Analysis
````

### 2. Launch in Google Colab

> Best used with Google Drive integration.

* Open `notebooks/organoid_analysis.ipynb`
* Update paths to your own brightfield and GFP images
* Run all cells


### 3. Launch with Conda or Python venv

* Create the conda env with this command:
  ```bash
  conda env create -f environment.yml
  conda activate organoid-env
  ```
* OR, create a python venv with thsi command:
  ```bash
  python -m venv organoid-env
  source organoid-env/bin/activate  # or .\organoid-env\Scripts\activate on Windows
  pip install -r requirements.txt
  ```  

### 4. Creating a loadable `jupyter-kernel`: This is needed as if we are runing the code from jupyter lab or VS-code we need to load python kenrnel

* A kernel can be created by the following command:
  ```python
  python -m ipykernel insatll --user --name organoid-env --display-name "organoid-env"
  ```

### 5. Launching the `organoid-env` environment

* We can launch the `organoid-env` conda env in two ways: 1. via anaconda prompt or 2. we can directly load the conda kernel in `VS-Code`
* 1. For anaconda prompt first open anaconda prompt:
     <img width="869" height="516" alt="image" src="https://github.com/user-attachments/assets/c3af3531-830a-4f39-874c-4253b2191c48" />
* 2. In the command line/terminal type in the following command:
  ```bash
  conda activate organoid-env
  ```
  then
  ```bash
  jupyter lab
  ```
  The `organoid-env` is loaded by default, but if its not loaded, we can select the kernel from the dropdown box on the top right hand.

* 3. Now you can directly run the `.ipynb` notebooks within the jupyter-lab or directly execute the python script from the command line.
  

## Output Example

* `.csv` file with organoid measurements
* Overlay image:

  * 🔵 Organoid outline
  * 🔴 GFP+ region (if applicable)

<p align="center">
  <img src="https://github.com/arka2696/HPC-Organoid-Quant/blob/main/Overlay-example.png" alt="Overlay Example" width="1000"/>
</p>

---

## Dependencies

All dependencies are standard and available in Google Colab:

* `OpenCV`
* `NumPy`
* `Matplotlib`
* `scikit-image`
* `Pandas`

If you want to run locally, create a `requirements.txt`:

```bash
pip install -r requirements.txt
```

---

## Notes

* The script accepts a broad format of images
* If your organoids are fragmented, the pipeline includes morphological merging to treat them as one object
* GFP quantification thresholds can be adjusted in the notebook

---

## Contact

For questions or suggestions, feel free to open an issue or reach out via GitHub.

---

## Citing the repo:

**v1.0.0 :** [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15738206.svg)](https://doi.org/10.5281/zenodo.15738206)

 *[Latest]* **v1.1.0 :** [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15756056.svg)](https://doi.org/10.5281/zenodo.15756059)

```bash
Cite as: Arkajyoti sarkar. (2025). HPC-Organoid-Quant (v1.0.0). Zenodo. https://doi.org/10.5281/zenodo.15738206
```


## License

[![License: CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc/4.0/)

This project is licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/).
