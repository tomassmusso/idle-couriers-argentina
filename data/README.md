# Data

The datasets used in this project are **not included** in this repository. They contain individual-level information about couriers, including GPS coordinates of each observation, and they are shared among the universities taking part in the initiative. Only aggregated results (tables and figures) are published here.

This folder describes the data so the analysis can be understood and, with access to the files, reproduced:

- `README.md` (this file): origin, structure and preparation of the datasets.
- [`data_dictionary.md`](data_dictionary.md): the variables used in the analysis.

## Origin

Both datasets were collected between September and October 2026 by students from several universities taking part in the initiative, and exported from Qualtrics. The analysis uses all final records collected up to October 31, 2026.

- **Field observations:** closed-ended forms filled in by students according to what they saw in public spaces (vehicle type, parking, courier activity, idle location, GPS position, among others).
- **Courier surveys:** a questionnaire for couriers about their working conditions. Participation was voluntary and respondents could skip questions. It was distributed through a QR code.

## Files used

| Dataset | File name | Size used in the analysis |
|---|---|---|
| Field observations | `ILI_Argentina_observations_2026-10-31.xlsx` | 1,760 records and 72 columns, after the geographic filter |
| Courier surveys | `ILI_Argentina_courier_survey_2026-10-31.xlsx` | 151 records and 56 columns |

The notebook accepts `.xlsx` or `.csv` files and tells the two datasets apart by their columns, so the exact file names are not required.

## How the datasets are linked

Each survey has an `ObservationID` that matches the `ResponseId` of a field observation. This link is only used for hypothesis 3 (waiting time by vehicle type), where the vehicle type comes from the linked observation. When several surveys share the same `ObservationID`, only one is kept.

## Preparation steps (done in the notebook)

1. The first row of the Qualtrics export, which contains the question texts, is removed. Real records are those whose `ResponseId` starts with `R_`.
2. Observations located outside Argentina are removed using their GPS coordinates (3 records).
3. Columns used in the analysis are renamed (see the data dictionary).
4. Duplicates are checked: there are no duplicated `ResponseId` values.
5. Records with missing values in the variables of a given analysis are excluded from that analysis only.

## Sample sizes in the analysis

| Analysis | n |
|---|---|
| Valid field observations | 1,760 |
| Courier surveys | 151 |
| Idle observations | 409 |
| Idle observations with a valid location (hypotheses 1 and 2) | 403 |
| Surveys with an answer on adverse conditions | 112 |
| Surveys linked to a motorcycle or bicycle/scooter observation (hypothesis 3) | 66 |
| Hypothesis 3, hours of waiting | 65 |
| Hypothesis 3, proportion of the workday spent waiting | 63 |

## Access

Access to the data depends on the initiative. To request it, contact the authors (see the main [README](../README.md)), who can point you to the right contact.

## Privacy

- The notebook uses GPS coordinates only to filter observations and to draw the heat map. The repository includes the heat map as a static image, not the coordinates.
- No individual responses are published.
