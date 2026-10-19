---
title: "Troubleshooting an Instrument-Air Compressor and Dryer Sequence"
date: 2026-10-08
draft: false

categories:
  - Field Notes

tags:
  - instrumentation
  - troubleshooting
  - instrument-air
  - compressor
  - dryer
  - pneumatic
---

We investigated an instrument-air compressor and dryer system where the compressor, dryer regeneration, drain valves, and pressure control were not operating as expected.

Initial symptoms included:

- Dryer not regenerating properly
- Water accumulating in the air system
- Drain valves not operating correctly
- Instrument-air leakage
- Compressor pressure cycling abnormally

Initial hypotheses included:

- Faulty solenoid valves
- Actuator problem
- Instrument-air leakage
- Pressure switch problem
- Electrical cable fault
- Incorrect sequence timing

During investigation, several individual faults were found.

A pressure switch cable was found mechanically damaged under a metal support. After repairing the damaged section, insulation resistance returned to a healthy value.

Several instrument-air leaks were also identified and rectified.

The dryer drain actuator was then tested with sufficient instrument air and was found to be mechanically stuck. The actuator was removed and cleaned, after which it operated properly.

However, the complete problem was still not resolved.

Further testing showed that the dryer behaved differently when sufficient external instrument air was available compared with operation using the compressor's own pressure.

The compressor pressure-switch settings and dryer sequence were then reviewed. The compressor was operating over a pressure range that did not properly support the dryer sequence. During part of the sequence, a drain command remained active while insufficient pressure was available, preventing the compressor from building pressure normally.

The pressure-switch settings were adjusted and the system was tested again.

The GTG compressor-dryer system was restored to normal operation. A separate sequence-timer issue remained on another dryer and was identified for further rectification.

## Key Lesson

A complex pneumatic package should not always be diagnosed by looking for a single faulty component.

A healthy compressor, solenoid, actuator, or pressure switch does not necessarily mean that the complete sequence is healthy.

The important troubleshooting chain is:

**Command → electrical output → solenoid → actuator → valve → process pressure → feedback → sequence transition**

A fault anywhere in this chain can appear as a fault somewhere else.

## Practical Troubleshooting Sequence

1. Confirm the actual operating sequence.
2. Check compressor start/stop pressure.
3. Check dryer sequence timing.
4. Verify solenoid operation electrically.
5. Verify actuator movement pneumatically.
6. Confirm valve movement.
7. Check for instrument-air leakage.
8. Verify pressure-switch operation and differential.
9. Compare command and actual feedback.
10. Test the complete sequence after individual component checks.

## Troubleshooting Principle

When several symptoms exist, do not assume that each symptom represents a separate root cause.

Reconstruct the physical sequence and identify where the intended sequence stops behaving normally.