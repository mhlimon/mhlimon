---
title: "Non-Invasive Blood Glucose Estimation Using a Multi-Sensor Portable and Wearable System"
date: 2020-03-12
draft: false
categories:
  - Publications
tags:
  - research
  - biomedical-instrumentation
  - sensors
  - machine-learning
  - signal-processing
description: "IEEE publication on a multisensor approach to non-invasive blood glucose estimation using PPG, GSR, temperature sensing, and a CNN model."
summary: "Research prototype combining multiple physiological sensors and a CNN-based estimator for non-invasive blood glucose estimation—not a clinical device."
publication:
  type: "conference"
  venue: "IEEE"
  doi: "https://doi.org/10.1109/GHTC46095.2019.9033119" 
---

## Summary

This paper presents a **multi-sensor**, **portable/wearable** engineering approach to **non-invasive blood glucose estimation**.

Conventional finger-prick glucometers remain widely used, but they are invasive. The project investigated whether a set of physiological measurements—processed computationally—could support glucose estimation without a blood sample.

The work sits at the intersection of **instrumentation**, **physiological sensing**, **signal processing**, and **machine learning**.

## Problem

Invasive glucose monitoring requires a blood sample. That cost, discomfort, and infection risk motivate research into non-invasive alternatives. Non-invasive estimation is difficult: physiological signals are noisy, person-dependent, and only indirectly related to glucose.

## System concept

The public description of the work includes:

| Element | Role |
|--------|------|
| **PPG** (photoplethysmography) | Optical peripheral signal |
| **GSR** (galvanic skin response) | Skin conductance-related signal |
| **Temperature** | Contextual physiological measurement |
| **Multisensor fusion / processing** | Combine channels into features for estimation |
| **CNN-based model** | Map processed inputs toward a glucose estimate |

The engineering goal was to study whether this combination can produce estimates **comparable in spirit** to invasive reference readings under the study conditions—not to claim a finished medical product.

## Method (high level)

1. Acquire signals from the selected sensors  
2. Preprocess and organize data for learning  
3. Train / evaluate a convolutional neural network estimator  
4. Compare estimates against invasive reference measurements used in the study  

Dataset size, demographics, error metrics, and validation protocol are defined in the paper—use those as the authoritative record.

## Contributions (engineering view)

- A **multisensor** hardware/software concept for non-invasive estimation research  
- Integration of sensing + learning rather than a single-sensor heuristic  
- A case study in how measurement quality and model validation limit performance  

## Limits (important)

- Research / prototype context  
- **Not** a clinically validated medical device  
- **Not** a substitute for regulated diagnostic equipment  
- Performance depends on data quality, population, protocol, and validation design  

Any medical use would require proper clinical validation and regulatory assessment.

## Link to later instrumentation work

The central lesson transfers directly to industrial I&C:

> **An algorithm is only as trustworthy as the measurements, assumptions, and validation behind it.**

A polished display or model cannot repair a weak sensor signal—whether the subject is glucose estimation or a 4–20 mA loop in a plant.

## Citation

**Title:** Non-invasive Blood Glucose Estimation Using Multi-sensor Based Portable and Wearable System  

**Publisher:** IEEE  

**Date:** 12 March 2020 (as recorded in the publication history)  

**IEEE Xplore:** [Document 9033119](https://ieeexplore.ieee.org/document/9033119)

Add DOI and full author list from the official record when you finalize the page.

## Read the paper

- [IEEE Xplore](https://ieeexplore.ieee.org/document/9033119)


## Related on this site

- [Projects — multisensor glucose estimation](/projects/non-invasive-blood-glucose/) 