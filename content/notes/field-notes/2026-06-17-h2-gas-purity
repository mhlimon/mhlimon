---
title: "Generator Hydrogen Purity Analyzer: Detector Failure, Calibration and Practical Lessons"
date: 2026-06-27
draft: false

description: "Field notes on troubleshooting a Yokogawa GD402/GD40 hydrogen purity analyzer, including detector failure, calibration philosophy and practical engineering lessons."

summary: "Practical lessons from troubleshooting a generator hydrogen purity analyzer using systematic fault isolation and OEM calibration procedures."

categories:
  - Field Notes

tags:
  - instrumentation
  - power-plant
  - generator
  - hydrogen
  - calibration
  - troubleshooting
  - yokogawa
  - gd402
  - gd40

cover:
  image: ""
  alt: "Generator Hydrogen Purity Analyzer"
  caption: ""
  relative: false

ShowToc: true
TocOpen: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowCodeCopyButtons: true
ShowWordCount: true
ShowShareButtons: false
comments: false
---

## Background

Hydrogen purity analyzers are essential instruments for hydrogen-cooled generators. Their purpose is to continuously monitor hydrogen purity to maintain efficient cooling and detect contamination by air or CO₂.

This field note summarizes engineering lessons learned while troubleshooting and calibrating a Yokogawa GD402 converter with a GD40 density detector. Plant-specific information has intentionally been omitted.

---

## Reported Symptoms

The analyzer exhibited the following symptoms:

- Hydrogen Purity Monitor Abnormal alarm
- Hydrogen Purity Low alarm
- Local converter showing Error-01
- Temporary Error-03
- Incorrect purity indication

---

## Investigation Strategy

Instead of replacing components randomly, the fault was isolated using controlled substitution.

1. Reset the converter.
2. Observe remaining alarms.
3. Replace the converter only.
4. Replace the detector only.
5. Verify using certified H₂ and CO₂ gases.
6. Perform OEM field calibration.
7. Restore the sampling circuit.
8. Verify with process gas.

This approach confirmed the failed component while avoiding unnecessary replacement of healthy equipment.

---

## Root Cause

The detector was responsible for **Error-01**.

Replacing only the converter did not remove the fault.

Replacing the detector immediately restored analyzer operation.

Later verification showed that the original converter remained serviceable after field calibration.

---

## Engineering Lessons

### Detector Constants Are Not Calibration

Replacement detectors include factory characterization constants.

Entering these constants identifies the detector but does **not** replace field calibration when the detector is installed with an existing converter.

---

### Pressure and Flow Serve Different Purposes

During calibration:

- **Flow** establishes the correct gas composition.
- **Pressure** verifies analyzer performance under operating conditions.

Understanding this distinction simplifies troubleshooting.

---

### Always Compare Compensated Density

OEM acceptance values are based on **compensated density**, not every density value displayed by the converter.

Always confirm which engineering value the procedure references.

---

### Verify Before Replacing

A structured component swap is often more valuable than replacing hardware based on assumptions.

Evidence should always guide maintenance decisions.

---

### Process Conditions Matter

During turning gear operation, reduced gas circulation can delay analyzer stabilization.

A slow purity increase after restoration does not necessarily indicate incorrect calibration.

---

## Practical Field Notes

- Fully open the vent valve during detector purging.
- Verify flowmeter engineering units before adjusting flow.
- Record pressure and differential pressure during calibration.
- Measure analog output whenever DCS and local indications disagree.
- Verify calibration gas quality before adjusting the analyzer.

---

## Key Takeaways

- Understand the measurement principle before calibrating.
- Separate detector characterization from field calibration.
- Use evidence-based troubleshooting.
- Verify analyzer performance under actual operating conditions.
- Consider process behaviour before questioning instrument accuracy.

---

## References

- Yokogawa GD402 Operation Manual
- Yokogawa GD402 Commissioning Manual
- Yokogawa GD40 Detector Manual
- Site calibration records
- Personal field observations