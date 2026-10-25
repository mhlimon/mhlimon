---
title: "Borewell Pump Operation Optimization Using Data-Driven Priority Selection"
date: 2025-09-21
draft: false
categories:
  - Field Notes
tags:
  - pump-optimization
  - energy-efficiency
  - dcs
  - data-analysis
  - control-logic
  - rotating-equipment
description: "A data-driven priority method for borewell pumps that balances efficiency, operating hours, and equipment wear—plus a staged path toward DCS use."
summary: "Weighted priority scoring for parallel borewell pumps (efficiency, hours balance, wear) with simulated energy impact and a phased implementation approach."
---

Multiple borewell pumps can often meet the same water demand, but they are not equal in efficiency, operating hours, or accumulated starts.

A simple lead/lag sequence can run reliably and still leave an open question:

**When several pumps can do the same duty, which available pump should start first?**

This note describes a **data-driven priority** approach for borewell pumps. The aim was not only to favour the most efficient machine, but to balance three requirements:

- reduce energy use  
- spread operating hours reasonably  
- limit starting-related wear  

Those factors are combined into a weighted priority score that can sit in a supervisory calculation and feed DCS start/stop selection—without replacing protection logic.

## 1. Initial data analysis

Seven active borewell pumps were reviewed using monthly operating data, including:

- running hours  
- average voltage and current  
- power factor  
- calculated power  
- flow rate  
- total water produced  
- total energy use  
- flow per unit power  

For the analysed period:

| Quantity | Value |
|----------|--------|
| Total water production | 14,523.58 m³ |
| Total energy consumption | 2,818.74 kWh |
| Average specific performance | ≈ 5.15 m³/kWh |

Individual pumps differed clearly in water delivered per unit energy. Treating every pump as equal can therefore waste energy.

## 2. Why efficiency alone is not enough

The most efficient pump should not necessarily run almost all the time.

If the system always picks the best efficiency unit, that pump can accumulate far more hours and starts than the others. Energy optimisation then becomes a second problem: **utilisation and wear**.

Selection was therefore split into three weighted factors:

| Factor | Weight | Objective |
|--------|--------|-----------|
| Efficiency | 50% | Favour lower energy per unit water |
| Operating-hour balance | 30% | Avoid concentrating runtime on one machine |
| Wear / health | 20% | Reflect starts and condition |

Weights are **engineering assumptions**. They should be reviewed after more operating data is collected.

## 3. Normalised scores

### Efficiency

Specific energy consumption:

$$
\mathrm{SEC}_i = \frac{\mathrm{Energy}_i}{\mathrm{Flow}_i}
$$

Lower SEC is better. A normalised efficiency score:

$$
E_i = 1 - \frac{\mathrm{SEC}_i - \mathrm{SEC}_{\min}}{\mathrm{SEC}_{\max} - \mathrm{SEC}_{\min}}
$$

If flow per power (m³/kWh) is used directly, it can be normalised so that **higher** performance scores higher.

### Operating-hour balance

Pumps with fewer accumulated hours score higher:

$$
H_i = 1 - \frac{\mathrm{Hours}_i - \mathrm{Hours}_{\min}}{\mathrm{Hours}_{\max} - \mathrm{Hours}_{\min}}
$$

This stops the most efficient pump from becoming permanently dominant.

### Wear / health

Starts can be an initial proxy. A richer score can later combine recent starts, trips, power factor, current vs baseline, vibration, bearing/motor temperature, and other available indicators.

An unhealthy pump must not be preferred only because it once looked efficient on paper.

## 4. Composite score and ranking

$$
S_i = 0.5\,E_i + 0.3\,H_i + 0.2\,W_i
$$

Pumps are ranked from highest \(S_i\) to lowest. From the analysed dataset, one ranking was:

**Pump-10 → Pump-8 → Pump-6 → Pump-7 → Pump-9 → Pump-5 → Pump-11**

The order is not permanent. It should be recalculated as conditions and health change.

## 5. Priority calculation vs sequencing

These are different jobs.

**Priority calculation (supervisory):**

```text
Operating data
  → Normalise parameters
  → Weighted score
  → Rank pumps
  → Publish priority order