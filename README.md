# Learning Time-Series Complexity for Life and Technology Detection

A contrastive representation learning project for **Caltech Ge/Ay 159**. We trained a 1D convolutional neural network to compare time series from abiotic, biotic, and technological sources, exploring whether their structure can be distinguished without choosing a hand-crafted complexity metric.

## Project outline

1. Collect environmental, physiological, and technological time series from public datasets and synthetic signals.
2. Divide recordings into overlapping windows and standardize each window.
3. Train a CNN to map windows into a 64-dimensional embedding space using contrastive learning.
4. Visualize the embeddings with PCA and t-SNE to compare source classes and individual signal families.

## Data and representation learning

The dataset includes **solar flares, river flow, temperature, and earthquakes** (abiotic); **heart rate, respiration, and EEG** (biotic); and **Morse code, RF signals, machine audio, and telemetry** (technological). Recordings are divided into 256-sample windows with a stride of 128, normalized within each window, and split by source record to avoid adjacent windows crossing train/test boundaries.

A three-layer **1D CNN** encodes each window as a unit-normalized 64-dimensional vector. Training uses two augmented views of each window (noise, amplitude scaling, and time shifts) and a **supervised contrastive loss**: windows from the same signal family are pulled together, while different families are separated. We trained with Adam for 20 epochs at a learning rate of `1e-3`. The model learns signal-family structure rather than directly predicting the three broad source classes.

## Results

**PCA and t-SNE** projections showed partial separation between abiotic, biotic, and technological signals, with clearer neighborhoods for individual signal families. Technological signals tended to form tighter clusters, while abiotic signals were more varied. EEG sometimes appeared closer to technological signals than to other physiological recordings.

These results suggest that learned time-series embeddings can capture differences in temporal organization. This was an exploratory experiment using Earth-based examples, **not a validated detector of extraterrestrial life or technology**. The findings are qualitative; clustering alone does not establish detection accuracy.

## Repository contents

| File | Contents |
| --- | --- |
| [`Ay159-Final-Project.ipynb`](Ay159-Final-Project.ipynb) | Data collection, preprocessing, contrastive training, and PCA/t-SNE visualizations |
| [`Ay159_Term_Paper.pdf`](Ay159_Term_Paper.pdf) | Project motivation, methodology, results, and discussion |
| [`README.md`](README.md) | Project overview |

## Authors

**Kahaan Gandhi and Rupali Batta**  
California Institute of Technology, **Ge/Ay 159**
