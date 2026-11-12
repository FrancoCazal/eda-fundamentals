# Data

## forestfires.csv

517 forest fires in Montesinho Natural Park, Portugal. Unchanged from the source.

- **Source:** Cortez, P. & Morais, A. (2007). *Forest Fires* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5D88D
- **Paper:** P. Cortez and A. Morais. A Data Mining Approach to Predict Forest Fires using Meteorological Data. Proceedings of the 13th EPIA, Portuguese Conference on Artificial Intelligence, 2007, pp. 512–523.
- **License:** CC BY 4.0.
- **Columns:** `X`, `Y` (map grid position), `month`, `day`, `FFMC`, `DMC`, `DC`, `ISI` (Fire Weather Index codes), `temp` (°C), `RH` (%), `wind` (km/h), `rain` (mm/m²), `area` (burned hectares). Notebook 06 explains each one.

## olympic-medalists.csv

39,783 Olympic medals won from Athens 1896 to Rio 2016, one row per medal won by one athlete.

- **Source:** rgriffin, *120 years of Olympic history: athletes and results*, Kaggle, https://www.kaggle.com/datasets/heesoo37/120-years-of-olympic-history-athletes-and-results. Data scraped from sports-reference.com in May 2018.
- **License:** CC0 (public domain).
- **Changes:** The original `athlete_events.csv` has 271,116 rows (one per athlete per event, with or without a medal) and 15 columns. This file keeps only the rows with a medal and only the columns the notebooks use, which also removes the athletes' names.
- **Columns:** `Age` (years), `Height` (cm), `Weight` (kg), `Year`, `Medal` (Gold, Silver or Bronze). Height and weight are missing for many early medalists.

## household-survey-2016.csv

37,814 people from Paraguay's household survey, as distributed in class.

- **Source:** Encuesta Permanente de Hogares (EPH) 2016, Dirección General de Estadística, Encuestas y Censos (DGEEC), now Instituto Nacional de Estadística (INE), Paraguay. The year comes from the ages and years of birth in the file.
- **License:** Published as public microdata by INE Paraguay. Credit INE as the source when reusing it.
- **Changes:** The class file has 58 columns. This one keeps the three the analysis uses. The survey microdata contain no names or identification numbers.
- **Columns:**
  - `P02`: age in years.
  - `ED06C`: code of the highest degree obtained. Notebook 03 uses 3 (primary school, *Educación Escolar Básica* up to 6th grade), 1 and 8 (university degrees), and 9 and 10 (postgraduate degrees).
  - `IPCM`: monthly household income per person, in guaraníes. **Kept exactly as in the class file**, including about 30,000 values inflated by a factor of 1000 when the file was imported with the wrong decimal separator. Notebook 03 shows how to detect them and corrects them.

## vehicle-permits-calbuco-2023.csv

7,948 payments of vehicle circulation permits in Calbuco, Chile, in 2023.

- **Source:** Municipalidad de Calbuco, *Permiso de Circulación Año 2023*, Portal de Datos Abiertos, https://datos.gob.cl/dataset/permiso-de-circulacion-agno-2023
- **License:** Open Data Commons Public Domain Dedication and License (PDDL).
- **Changes:** The class file has 23 columns. This one keeps four, renamed in English. The removed columns include the plate number, its check digit and the SII vehicle code, which identify individual vehicles. The class copy has 7,948 rows; the portal's current version has 10,800.
- **Columns:**
  - `vehicle_group`: `Vehiculo Liviano` (light vehicle), `Transporte Publico` (public transport) or `Carga` (cargo).
  - `vehicle_year`: year the vehicle was built.
  - `payment_channel`: `Presencial` (in person) or `Internet` (online).
  - `amount_paid`: amount paid, in Chilean pesos (CLP). A permit paid in two installments appears as two rows.
