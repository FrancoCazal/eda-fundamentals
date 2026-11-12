# Exploratory Data Analysis Fundamentals

Exercises from the Probability and Statistics Lab (*Laboratorio de Probabilidad y Estadística*) at FIUNA (Facultad de Ingeniería, Universidad Nacional de Asunción), 2023, second cycle (*segundo ciclo*).

The lab taught descriptive statistics on real datasets, first in Excel and then in Python with pandas and matplotlib. This repository collects my work as six notebooks. Each analysis shows the Excel formula next to the pandas code that does the same thing, so it can be followed from either side.

## Notebooks

GitHub shows the notebooks with their tables and charts, so they can be read without running anything.

| # | Notebook | Data | What it covers |
|---|---|---|---|
| 01 | [pandas basics](notebooks/01-pandas-basics.ipynb) | Olympic medals | Loading a CSV, `head` and `tail`, missing values with `dropna` and `fillna`, selecting with `loc`, boolean filters |
| 02 | [Ages of Olympic medalists](notebooks/02-olympic-medalist-ages.ipynb) | Olympic medals, 1896–2016 | Descriptive statistics for two periods, a frequency table, histograms in one chart |
| 03 | [Household income and education in Paraguay](notebooks/03-household-income.ipynb) | Household survey, 2016 | Finding and fixing values inflated by a decimal-separator error, then comparing incomes by education level |
| 04 | [Vehicle permit payments](notebooks/04-vehicle-permits.ipynb) | Calbuco, Chile, 2023 | Eight segments built with boolean masks, statistics per segment, a log-scale chart |
| 05 | [Least-squares fitting](notebooks/05-least-squares.ipynb) | Small exercise datasets | A parabola and a line from the normal equations, r², a check against `np.polyfit` |
| 06 | [Forest fires](notebooks/06-forest-fires.ipynb) | UCI Forest Fires | A full exploratory analysis: seasonality, a very skewed variable and its log transform, a correlation matrix, counts on a map grid |

## Running the notebooks

```sh
python -m venv .venv
source .venv/bin/activate        # on Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

The notebooks read their data from [`data/`](data/) with relative paths, so they run from the `notebooks/` folder, which is where Jupyter starts them. The [workflow](.github/workflows/notebooks.yml) executes all six on every push.

## Excel and pandas

| Excel | pandas | Note |
|---|---|---|
| `=COUNT(range)` | `s.count()` | Both skip empty cells or `NaN` |
| `=AVERAGE(range)` | `s.mean()` | |
| `=MEDIAN(range)` | `s.median()` | |
| `=MODE(range)` | `s.mode()` | pandas returns every tied value; Excel returns the first one it finds |
| `=STDEV(range)` | `s.std()` | Both are the sample standard deviation (divide by n − 1) |
| `=MAX(range)`, `=MIN(range)` | `s.max()`, `s.min()` | |
| `=COUNTIFS(r,">="&a,r,"<"&b)` per class | `pd.cut(s, bins, right=False).value_counts()` | `right=False` puts the lower limit in the class |
| `=IF(cond, x, y)` | `x.where(cond, y)` | |
| AutoFilter, then copy the visible rows | `df[condition]` | |
| `=CONCATENATE(...)` to label a group | masks combined with `&`, `\|` and `~` | |
| Clustered column chart | `df.plot(kind="bar")` | |

## Data

| File | Source | License |
|---|---|---|
| `forestfires.csv` | Cortez & Morais (2007), UCI Machine Learning Repository | CC BY 4.0 |
| `olympic-medalists.csv` | "120 years of Olympic history", Kaggle | CC0 |
| `household-survey-2016.csv` | Encuesta Permanente de Hogares 2016, INE Paraguay | Public microdata, credit INE |
| `vehicle-permits-calbuco-2023.csv` | Municipalidad de Calbuco, datos.gob.cl | ODC PDDL |

Three of the files are trimmed copies of the originals, and the vehicle file has the plates and other vehicle identifiers removed. [`data/README.md`](data/README.md) lists the columns of each file and every change.

## What is not here

The lab's own material stays with the course: slides, exercise statements, spreadsheet templates and the instructors' files. So does the dataset of the graded workshops, which the course created. Every problem description here is in my own words.

## License

The code is under the [MIT License](LICENSE). Each data file keeps its source's license.
