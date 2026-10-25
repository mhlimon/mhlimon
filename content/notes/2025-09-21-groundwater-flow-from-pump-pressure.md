---
title: "Developing a DCS-Based Groundwater Consumption Measurement from Pump Pressure"
date: 2025-09-21
draft: false
categories:
  - Field Notes
tags:
  - instrumentation
  - dcs
  - ovation
  - flow-measurement
  - ultrasonic-flowmeter
  - pump-characterization
  - groundwater
description: "Using temporary ultrasonic flow measurement to characterize borewell pumps and implement estimated groundwater flow and daily consumption in the Ovation DCS from discharge pressure."
summary: "No permanent flowmeters on borewell discharges—portable ultrasonic characterization under 1–3 pump operation, then pressure + pump-count based flow estimation and volume totals in the DCS."
---

Eight borewell pumps (numbered 4–11) discharged into a **common underground header**. The DCS had pump status and discharge pressure—but **no permanent flowmeters** on the individual lines.

That left a clear operational gap: pressure and running status were visible; **groundwater production was not**.

Fitting a permanent flowmeter on every line was not practical in the time available. The problem was treated as **measurement characterization**: can existing pressure (plus running status) support a usable estimate of flow for monitoring?

A portable ultrasonic flowmeter was used to map pressure–flow behaviour under different operating counts. Those relationships were implemented in the **Ovation** DCS as calculated flow, then integrated to daily and cumulative consumption.

## 1. Existing system

| Item | Detail |
|------|--------|
| Pumps | Pump-4 … Pump-11 (eight units) |
| Out of service during campaign | Pump-4 |
| Header | Common underground header |
| Max simultaneous pumps | Three |
| Available in DCS | Running status, discharge pressure, history |
| Missing | Direct flow |

## 2. Reference instrument

| Parameter | Detail |
|-----------|--------|
| Type | Portable ultrasonic flowmeter |
| Model | FSSE1EC1-BY |
| Calibration date | 17 December 2024 |
| Role | Temporary reference only—not a permanent installation |

Purpose: answer *what flow corresponds to measured discharge pressure under defined operating conditions?*

## 3. Field method

Measurements under three conditions:

1. One pump running  
2. Two pumps running  
3. Three pumps running  

For each condition, discharge/header pressure and ultrasonic flow were recorded at several points.

Because all discharges share a header, the hydraulic operating point **changes** when more pumps run. One universal curve for all states is not justified.

```text
Operating condition + header pressure
        → measured ultrasonic flow
        → pressure–flow data
        → characteristic per pump count