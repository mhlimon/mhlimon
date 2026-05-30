---
title: "Troubleshooting an Ovation DCS Analog Input Bad Value"
date: 2026-05-24
draft: false

categories:
  - Field Notes

tags:
  - instrumentation
  - dcs
  - troubleshooting
---
Today I investigated a CT fan motor current feedback issue in an Emerson Ovation DCS where the analog input showed BAD VALUE with frozen low current indication.

Initial checks suggested either:

AI channel failure
Current transducer issue
Open 4–20 mA loop

Field ammeter indicated normal motor current, which confirmed the actual process was healthy.

After tracing the signal path and comparing with a healthy loop, a loose cable termination inside the switchgear was identified. Replacing the cable lugs and tightening the terminals restored a stable 15 mA signal and normal DCS indication.

Key Lesson

In analog instrumentation loops, unstable or frozen DCS values are not always caused by transmitters or AI cards. Loose terminations and intermittent loop continuity issues can produce misleading symptoms that imitate hardware failure.

Practical Troubleshooting Sequence

DCS indication → AI raw value → field verification → loop tracing → comparative checking → terminal inspection.