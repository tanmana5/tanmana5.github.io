---
title: "Mapping the Wild: A Read on Geospatial Foundation Models for Ecology"
date: 2026-06-04
description: "Paper review — what geospatial foundation models bring to ecological mapping, and where the abstraction still leaks."
tags: [paper-review, geospatial, foundation-models, ecology, remote-sensing]
---

A quick read of *Ecological Mapping with Geospatial Foundation Models*. The paper takes two pre-trained geospatial foundation models — **Prithvi-EO-2.0** and **TerraMind** — and fine-tunes them for three ecological mapping tasks. Notes below on the training setup, the modality choices, and (most interesting to me) how the authors constructed ground truth for tasks where direct labels barely exist.

## Overview

Both Prithvi-EO-2.0 and TerraMind are foundation models pre-trained on massive, unlabeled global satellite datasets to learn general patterns of the Earth's surface. In this paper, the authors take those pre-trained weights and run targeted fine-tuning passes to adapt them to specialized ecological tasks.

## Downstream tasks

The models were fine-tuned across three ecological use cases and compared against traditional deep-learning baselines:

- **Forest functional trait mapping** — pixel-level segmentation of forest canopies to classify leaf forms (needle-leaf, broad-leaf, mixed-leaf) and canopy cover density.
- **Peatlands detection** — segmenting and isolating sensitive peatland ecosystems from surrounding land cover.
- **Land use / land cover (LULC) generation** — testing TerraMind's generative capabilities to "fill in the blanks" and map out land classifications when satellite data layers are missing.

## Training setup

**Hardware and optimizer.** Fine-tuning ran on a single NVIDIA A100-80GB GPU, using the **AdamW** optimizer with a learning rate of $1 \times 10^{-4}$ and weight decay of $5 \times 10^{-2}$. A **dice loss** was used to handle the pixel-level segmentation boundaries.

**Modality differences.** A key takeaway from the training phase is how the two models were fed data:

- **Prithvi-EO-2.0** — *unimodal* fine-tuning using 12 spectral bands from Sentinel-2 imagery.
- **TerraMind** — both *unimodal* and *multimodal* fine-tuning, where the multimodal variant was trained on fused stacks of Sentinel-1 radar, Sentinel-2 optical, RGB, NDVI (vegetation index), and DEM (digital elevation models) simultaneously.

## Ground truth construction

The most interesting part of the paper is how the authors actually built ground truth labels — particularly for peatlands, where direct labels are essentially nonexistent at scale.

### Task 1: Forest functional traits

For this task, the researchers focused on segmenting **leaf forms** (e.g. broadleaf vs. needle-leaf) and **canopy cover density**.

- **Field source:** **NEON (National Ecological Observatory Network)** — an NSF-sponsored program that collects long-term, rigorous field-based ecological data across the United States.
- **Labels:** The authors correlated satellite data with the **Copernicus Land Monitoring Service Global Dynamic Land Cover** dataset, which provides yearly global LULC estimates across 23 classes. From these they isolated **12 forest categories** — defined by canopy density, leaf retention, and leaf form — to serve as the definitive ground truth labels at NEON sites.

### Task 2: Peatlands detection

Peat bogs are vital for global carbon sequestration but are notoriously difficult to track from space. The authors focused on **Karukinka Nature Park** in southern Patagonia (Chile) alongside four other global peatland clusters, combining four distinct data sources to synthesize a highly accurate ground truth label set:

1. **PEATGRIDS** — the foundational source. A globally recognized, open-source resource that maps estimated **peat thickness and carbon stocks** across the Earth at a $1 \times 1\text{ km}$ resolution grid.
2. **Copernicus LULC (2020) high-resolution maps** — used to sharpen the blurry $1\text{ km}$ PEATGRIDS data down to a granular $10\text{-meter}$ resolution. The authors isolated the *"herbaceous vegetation"* and *"herbaceous wetland"* classes, which strongly correlate with physical peat moss (*Sphagnum magellanicum*).
3. **NDVI thresholding** — local NDVI layers computed from Sentinel-2 composites, filtered with a strict threshold ($0.23$ to $0.8$) to isolate living peat-moss signatures. The final binary mask was defined where positive PEATGRIDS data intersected with positive high-resolution NDVI layers.
4. **Topographical filtering** — to eliminate false positives, the labels were crossed with elevation data and any pixel above **450 m altitude** or on a slope steeper than **10°** was removed, since peatlands cannot physically form on mountain peaks or steep cliffs.

## Results

Both fine-tuned foundation models outperformed traditional deep-learning baselines like ResNet-101 across all three tasks, with **TerraMind's multimodal variant yielding the highest accuracy gains**. The localized fine-tuning paid off — and the multimodal data fusion proved to be the decisive ingredient.

## References

- [Ecological Mapping with Geospatial Foundation Models](https://arxiv.org/pdf/2602.10720)
