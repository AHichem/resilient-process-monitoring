# Resilient process monitoring for an industrial fermentation

Monitoring models that still work when sensors drift, fail or go missing, built on 100 batches of a simulated 100,000 L penicillin fermentation (IndPenSim).

## Why this matters

In biopharmaceutical manufacturing, every batch is expensive and quality must be demonstrated, not assumed. Statistical process monitoring flags a batch that is drifting before it is lost. In a real plant, however, the monitoring model itself faces problems: sensors drift or freeze, values go missing, and operating conditions change. A model that raises false alarms or misses faults in those situations is not usable. This project studies how to build monitoring that stays reliable.

## Roadmap

| Notebook | Content | Status |
|---|---|---|
| 01 | Load IndPenSim, sanity checks, first look at the 100 batches | Done |
| 02 | Golden batch and batch trajectories by control strategy | Planned |
| 03 | Multivariate statistical process monitoring: PCA, Hotelling T² and SPE (Q) charts on normal batches | Planned |
| 04 | Fault detection on batches 91-100: detection rate, false alarm rate, detection delay | Planned |
| 05 | Resilience tests: inject sensor bias, drift, frozen values and missing data, and measure how the monitor degrades | Planned |
| 06 | Making it robust: robust scaling, sensor-fault isolation, ML-based monitoring and adaptive retraining | Planned |

## Data

[IndPenSim](https://data.mendeley.com/datasets/pdnjz7zz5x) (Goldrick et al.), licence CC BY 4.0. 100 fed-batch runs: batches 1-30 recipe-driven, 31-60 operator-controlled, 61-90 controlled by an APC using Raman spectroscopy, 91-100 containing process faults.

The data (about 2.5 GB) is not stored in this repository. Notebook 01 downloads it from Mendeley and caches a compact copy of the process variables in Google Drive.


## References

- Goldrick S., Stefan A., Lovett D., Montague G., Lennox B. (2015). The development of an industrial-scale fed-batch fermentation simulation. *Journal of Biotechnology*, 193, 70-82.
- Goldrick S., Duran-Villalobos C., Jankauskas K., Lovett D., Farid S. S., Lennox B. (2019). Modern day monitoring and control challenges outlined on an industrial-scale benchmark fermentation process. *Computers and Chemical Engineering*, 130, 106471.


