# Idle Couriers in Argentina

Analysis of where informal couriers wait between orders in Argentina and the adverse conditions they report, based on 1,760 field observations and 151 courier surveys.

## Key findings

- Two-wheeled vehicles accounted for 77.9% of the classified vehicles observed: motorcycles (838 observations) and bicycles or scooters (522 observations).
- 95.5% of the 112 couriers who answered the question reported at least one adverse condition during their typical shifts, mainly back, neck, arm or leg pain (57.1%), exposure to heat, cold or rain (53.6%), insecurity (41.1%) and fatigue (36.6%).
- Almost 8 out of 10 idle records (78.7%) were located on the street or directly outside a business (317 of 403; 95% CI: 74.4%–82.4%).

## Report

The report *Urban Spatial Organization of Couriers During Idle Periods* is in [`report/`](report/). An extended version covering all three hypotheses will be added there.

## Repository structure

```
idle-couriers-argentina/
├── README.md
├── LICENSE
├── .gitignore
├── requirements.txt
├── report/
│   ├── Urban_Spatial_Organization_of_Couriers_During_Idle_Periods.pdf
│   └── Urban_Spatial_Organization_of_Couriers_During_Idle_Periods_extended.pdf  (to be added)
├── notebooks/
│   └── analysis.ipynb
├── figures/
│   ├── fig1_heatmap.png
│   ├── fig2_vehicle_types.png
│   ├── fig3_parking.png
│   ├── fig4_adverse_conditions.png
│   └── fig5_idle_locations.png
└── data/
    ├── README.md
    └── data_dictionary.md
```

- `report/`: the report (PDF).
- `notebooks/analysis.ipynb`: the full analysis, with its outputs.
- `figures/`: the figures used in the report.
- `data/`: description of the datasets and a data dictionary (the data themselves are not included).

## Data

The analysis uses two datasets collected between September and October 2026 by students from several universities taking part in the initiative:

- **Field observations:** 1,760 valid records (after excluding observations located outside Argentina).
- **Courier surveys:** 151 responses, voluntary and collected through a QR code.

The data are **not included** in this repository: they contain individual-level and location information about couriers and are shared among the participating universities. See [`data/README.md`](data/README.md) for the structure of each dataset and [`data/data_dictionary.md`](data/data_dictionary.md) for the variables used.

## Methods

All tests use a 5% significance level, with 1% and 10% as robustness checks.

- **H1 (idle location):** one-tailed exact binomial test against p = 0.50, with a Wilson 95% confidence interval.
- **H2 (vehicle type and idle location):** chi-square test of independence, with Cramér's V as effect size. The association is statistically significant but weak.
- **H3 (waiting time, motorcycles vs. bicycles/scooters):** Mann-Whitney U test on survey data, for two outcomes (waiting hours and proportion of the workday spent waiting), with Cohen's d and Welch confidence intervals. No significant difference was found.

## Limitations

- The sample is not random: data were collected in specific zones and at specific times, so the results describe the records collected, not all couriers.
- The design is observational: it shows patterns, not causes.
- The data show where couriers are idle, but not whether they are resting or waiting for an order, for how long, or why.
- Independence between observations is assumed.
- Survey participation was voluntary.

## Authors and acknowledgements

Developed by Tomás Musso, Danilo Birocho, students at Universidad de Palermo (UP), as part of the MIT Informal Logistics Initiative (ILI). Fieldwork data were collected by students from several participating universities. 

This is a student project and not an official publication of MIT. AI tools were used to help write Python code and to correct spelling and grammar, since English is not our native language; the analysis and interpretation are the authors' own.

## License

The code is released under the MIT License (see `LICENSE`; unrelated to the Massachusetts Institute of Technology). The report and figures are © the authors, all rights reserved. The data are not included and are not covered by this license.
