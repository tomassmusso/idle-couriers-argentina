# Data dictionary

This dictionary describes only the variables used in the analysis. The full datasets have more columns (72 in the field observations and 56 in the courier surveys).

Notes:

- Column names are those of the original files. "Name in notebook" is the name given in the analysis.
- Descriptions are paraphrased and are not the literal wording of the questionnaires.
- Response labels in the data are in Spanish and some include emojis; the English names below are the ones used in the report and figures.
- `Q` numbers refer to the questions of the project's field form and courier survey.

## Field observations

| Column | Name in notebook | Type | Description | Used in |
|---|---|---|---|---|
| `ResponseId` | – | Text | Unique ID of the observation (starts with `R_`). Key to link with the surveys. | All analyses |
| `GPS_Latitude` | `latitud` | Numeric | Latitude of the observation. | Geographic filter, heat map (aggregated image only) |
| `GPS_Longitude` | `longitud` | Numeric | Longitude of the observation. | Geographic filter, heat map (aggregated image only) |
| `Q8` | `tipo_vehiculo` | Categorical | Vehicle type observed: motorcycle, bicycle or scooter, medium truck, heavy truck, pickup truck, car, SUV, van, other. | Figure 2, Figure 3, hypotheses 2 and 3 |
| `Q12` | `estacionamiento_legal` | Categorical | How the vehicle was parked: legal, or illegal with the type of violation (on the sidewalk, on the street or double-parked, on a crosswalk or bike lane). | Figure 3 |
| `Q23` | `actividad` | Categorical | Activity of the courier at the moment of the observation. Records with the idle ("Inactivo") status form the sample for the idle analyses. | Figure 3, hypotheses 1 and 2 |
| `Q28` | `lugar_inactividad` | Categorical | Where the idle courier was: on the street, outside a business, in a public park, other. | Figure 5, hypotheses 1 and 2 |

## Courier surveys

| Column | Name in notebook | Type | Description | Used in |
|---|---|---|---|---|
| `ResponseId` | – | Text | Unique ID of the survey (starts with `R_`). | Survey counts |
| `ObservationID` | – | Text | ID of the field observation the survey is linked to (matches `ResponseId` in the field observations). | Hypothesis 3 |
| `Q3_HORAS_TRABAJO_1` | `horas_trabajo` | Numeric (hours) | Hours the courier reports working per day. | Hypothesis 3 (proportion of the workday spent waiting) |
| `Q4_HORAS_DESCANSO_1` | `horas_descanso` | Numeric (hours) | Hours the courier reports resting per day. | Hypothesis 3 (proportion of the workday spent waiting) |
| `Q5_HORAS_IMPRODUCTIV_1` | `horas_espera` | Numeric (hours) | Hours the courier reports waiting per day for lack of orders. | Hypothesis 3 |
| `Q14_CONDICIONES` | `condiciones_adversas_survey` | Multiple choice (text) | Adverse conditions the courier experiences during typical shifts: back, neck, arm or leg pain; exposure to heat, cold or rain; insecurity; fatigue; pressure to deliver quickly; lack of access to drinking water; long unpaid waits; lack of places to rest; other; none. | Figure 4 |

## Variables derived in the notebook

| Variable | Built from | Definition | Used in |
|---|---|---|---|
| Idle sample | `actividad` | Observations whose activity is idle. | Figure 3, hypotheses 1 and 2 |
| Binary location (H1) | `lugar_inactividad` | 1 = on the street or outside a business; 0 = public park or other. | Hypothesis 1 |
| Vehicle group (H2) | `tipo_vehiculo` | Three groups: bicycle or scooter, motorcycle, other motorized vehicles. | Hypothesis 2 |
| Location group (H2) | `lugar_inactividad` | Three groups: on the street, outside a business, public park or other. | Hypothesis 2 |
| Vehicle group (H3) | `tipo_vehiculo` (from the linked observation) | Two groups: motorcycle, bicycle or scooter. Other vehicles are excluded. | Hypothesis 3 |
| Parking type | `estacionamiento_legal` | Legal; illegal on the sidewalk; illegal on the street or double-parked; illegal on a crosswalk or bike lane. Records with "other" or no data are excluded. | Figure 3 |
| Y1: hours of waiting | `horas_espera` | Daily hours of waiting. | Hypothesis 3 |
| Y2: proportion of waiting | `horas_espera`, `horas_trabajo`, `horas_descanso` | Waiting hours divided by the total workday (work + rest + waiting). | Hypothesis 3 |

## Missing values

Records with missing values in the variables of a given analysis are excluded from that analysis only, so the sample size changes between analyses (see the table of sample sizes in [`README.md`](README.md)).
