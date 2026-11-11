# Resilient process monitoring for an industrial fermentation

Monitoring models that still work when sensors drift, fail or go missing, built on 100 batches of a simulated 100,000 L penicillin fermentation (IndPenSim).

## Why this matters

In biopharmaceutical manufacturing, every batch is expensive and quality must be demonstrated, not assumed. Statistical process monitoring flags a batch that is drifting before it is lost. In a real plant, however, the monitoring model itself faces problems: sensors drift or freeze, values go missing, and operating conditions change. A model that raises false alarms or misses faults in those situations is not usable. This project studies how to build monitoring that stays reliable.

## Roadmap

| Notebook | Content | Methods | Status |
|---|---|---|---|
| 01 | Load IndPenSim, sanity checks, first look at the 100 batches | Data validation, exploratory analysis | Done |
| 02 | Golden batch and batch trajectories by control strategy; can the batch groups and fault types be found without labels? | Batch alignment, mean ± 3σ envelope, **K-means** | Planned |
| 03 | Multivariate statistical process monitoring, trained on normal batches only | **PCA**, Hotelling T² and SPE (Q) charts, control limits | Planned |
| 04 | Fault detection on batches 91-100 | Detection rate, false alarm rate, detection delay, alarm threshold trade-off | Planned |
| 05 | Resilience tests: inject sensor bias, drift, frozen values and missing data, and measure how the monitor degrades | Fault injection, contribution plots for fault isolation | Planned |
| 06 | Comparing detectors, including on fault types never seen in training; robustness to a change of control strategy | **PCA vs Isolation Forest vs Random Forest vs XGBoost**, grouped cross-validation by batch, robust scaling, adaptive retraining | Planned |
| 07 (optional) | Soft sensor: predict penicillin from online sensors, and test its robustness to sensor faults | Random Forest regression | Optional |

## Key findings so far

- The raw file contains three labelling errors (swapped columns, a `Batch ID` and a `Fault flag` that are neither); the batch identifier is validated against the time resets at every load.
- Batch duration and penicillin alone are not fault indicators: faulty batches stay within the normal duration range, and many fault-free batches also show a penicillin drop after ~150 h.
- Faults are intermittent and start part-way through the batch, which makes detection delay a key metric.
- APC-controlled batches are the most reproducible; recipe and operator batches split into two families.

## Data

[IndPenSim](https://data.mendeley.com/datasets/pdnjz7zz5x) (Goldrick et al.), licence CC BY 4.0. 100 fed-batch runs: batches 1-30 recipe-driven, 31-60 operator-controlled, 61-90 controlled by an APC using Raman spectroscopy, 91-100 containing process faults.

The data (about 2.5 GB) is not stored in this repository. Notebook 01 downloads it from Mendeley and caches a compact copy of the process variables in Google Drive.


## References

- Goldrick S., Stefan A., Lovett D., Montague G., Lennox B. (2015). The development of an industrial-scale fed-batch fermentation simulation. *Journal of Biotechnology*, 193, 70-82.
- Goldrick S., Duran-Villalobos C., Jankauskas K., Lovett D., Farid S. S., Lennox B. (2019). Modern day monitoring and control challenges outlined on an industrial-scale benchmark fermentation process. *Computers and Chemical Engineering*, 130, 106471.


