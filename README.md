
# Resting-State EEG Analysis: Eyes Open vs. Eyes Closed

## Overview

This project analyzes two short resting-state EEG recordings to investigate differences in brain activity between eyes-open and eyes-closed conditions. The analysis focuses on time-domain signals, power spectral density (PSD), frequency-band power, and the spatial distribution of alpha activity.

The project uses **EEGLAB** for graphical analysis and **MNE-Python** for reproducible, code-based analysis.

## Research Question

**What changes in EEG activity occur when the eyes close?**

The analysis examines posterior alpha activity, spectral patterns, scalp topography, and potential non-neural artifacts. Observations are quantified before being interpreted.

## Dataset

The recordings are from the [PhysioNet EEG Motor Movement/Imagery Dataset](https://physionet.org/content/eegmmidb/1.0.0/), Subject S001.

| File | Condition | Duration | EEG Channels | Sampling Rate |
|---|---|---|---|---|
| `S001R01.edf` | Eyes open | Approximately 60 seconds | 64 | 160 Hz |
| `S001R02.edf` | Eyes closed | Approximately 60 seconds | 64 | 160 Hz |

## Methods

### 1. EEGLAB: GUI-Based Analysis

The EEGLAB workflow includes:

- Importing EEG recordings in EDF format.
- Loading the 64-channel electrode-location file.
- Inspecting raw EEG signals at Fz, Cz, Pz, and Oz.
- Applying average reference to a copy of each dataset.
- Computing power spectral density (PSD) in the 1–45 Hz range.
- Visualizing scalp activity around 10 Hz.
- Comparing spectral patterns between conditions.

### 2. MNE-Python: Code-Based Analysis

The Python workflow includes:

- Loading and inspecting both EEG recordings.
- Cleaning channel labels by removing trailing periods.
- Matching electrode labels to the `standard_1005` montage using case-insensitive matching.
- Plotting raw EEG signals from Fz, Cz, Pz, and Oz.
- Applying average reference to a copy of each recording.
- Estimating PSD using Welch's method.
- Calculating spectral features for each channel and condition.
- Generating scalp maps of alpha-band power.
- Comparing Oz spectrograms between conditions.
- Exporting spectral features to a CSV file.

## Analysis Parameters

| Parameter | Setting |
|---|---|
| PSD frequency range | 1–45 Hz |
| Welch window | Hann |
| Welch window length | 4 seconds |
| Welch overlap | 50% |
| Welch `n_fft` | 1024 |
| Spectrogram window | 2 seconds |
| Spectrogram overlap | 75% |
| Spectrogram `n_fft` | 512 |

## Frequency Bands

| Band | Frequency Range |
|---|---|
| Delta | 1–4 Hz |
| Theta | 4–8 Hz |
| Alpha | 8–13 Hz |
| Beta | 13–30 Hz |

## Expected Outputs

- Raw EEG time-series plots.
- PSD comparisons between eyes-open and eyes-closed conditions.
- Absolute and relative frequency-band power.
- Alpha-peak frequency estimates.
- Scalp maps of alpha-band power for both conditions.
- A closed-minus-open alpha-power difference map.
- Oz spectrograms for both conditions.
- A CSV file containing channel-level spectral features.

## Tools and Technologies

- Python
- MNE-Python
- NumPy
- SciPy
- pandas
- Matplotlib
- EEGLAB
- Jupyter Notebook / Google Colab

## Interpretation

Eyes-closed resting EEG commonly shows stronger posterior alpha activity than eyes-open EEG. This project investigates whether that pattern is observable in the selected recordings. Results should be interpreted in the context of recording duration, preprocessing choices, and possible artifacts.

## References

- [PhysioNet EEG Motor Movement/Imagery Dataset](https://physionet.org/content/eegmmidb/1.0.0/)
- [MNE-Python Documentation](https://mne.tools/stable/)
- [EEGLAB Documentation](https://eeglab.org/)

---

*This project was completed as part of an EEG signal-processing learning assignment.*
