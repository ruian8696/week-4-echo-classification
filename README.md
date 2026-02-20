# week-4-echo-classification
# Week 4 – Echo Classification (Lead vs Sea Ice)

This repository contains the Week 4 assignment for echo classification using **unsupervised learning (GMM)**.

## Task
1. Classify SAR echoes into **Lead** and **Sea Ice**
2. Compute **average echo shape** and **standard deviation** for the two classes
3. Compare the predicted classes with the **ESA official classification** using a **confusion matrix**

## Data
- `standard_measurement.nc` (ESA labels, including surface type class)
- `enhanced_measurement.nc` (waveforms and additional variables)

> Data files are not uploaded to GitHub due to size.  
> The notebook expects the `.nc` files to be available in Google Drive (Colab).

## Method (Summary)
- Load waveform data (`waveform_20_ku`) and selected features (e.g., `sig0_water_20_ku`, peakiness, waveform spread).
- Standardize features and apply a **2-component Gaussian Mixture Model (GMM)**.
- Map the two clusters to **Lead / Ice** by maximizing agreement with ESA labels on the filtered subset.
- Evaluate using confusion matrix + classification report.
- Compute mean and std waveform shapes for each predicted class (normalized waveforms).

## Repository structure
- `week-4-echo-classification.ipynb` – main analysis notebook
- `results/` – output figures and files:
  - `confusion_matrix.png`
  - `mean_std_echo_LEAD_vs_ICE.png`
  - `classification_report.txt`
  - `summary.txt`
  - `lead_mean.csv`, `lead_std.csv`, `ice_mean.csv`, `ice_std.csv`
- `requirements.txt` – Python dependencies

## Results (Quick view)
### Confusion Matrix (ESA vs GMM)
See: `results/confusion_matrix.png`

### Mean echo shapes (Lead vs Ice)
See: `results/mean_std_echo_LEAD_vs_ICE.png`

## How to run (Google Colab)
1. Open `week-4-echo-classification.ipynb` in Colab
2. Mount Google Drive
3. Set paths to:
   - `standard_measurement.nc`
   - `enhanced_measurement.nc`
4. Run all cells to reproduce figures in `results/`

## Notes
- Labels used from ESA surface type class:
  - Lead = 2
  - Ice = 3
