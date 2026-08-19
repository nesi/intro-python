# Datasets

## Portal teaching database (Data Carpentry, python-ecology-lesson)

| File | Rows | Description |
| --- | --- | --- |
| `surveys.csv` | 35549 | Individual rodent captures from the Portal Project (Chihuahuan Desert, Arizona). |
| `species.csv` | 54 | Species codes used by `surveys.csv`, with genus, species and taxa. |

Source: <https://datacarpentry.org/python-ecology-lesson/> (Portal Project
teaching database, <https://doi.org/10.6084/m9.figshare.1314459>).

## Gapminder

Life expectancy, population and GDP per capita by country and year (1952-2007,
five-year intervals).

### Tidy (long) format

| File | Rows | Columns |
| --- | --- | --- |
| `gapminder.csv` | 1704 | `country`, `year`, `pop`, `continent`, `lifeExp`, `gdpPercap` |

One row per country-year. This is the shape to use with `plotnine`, and the
usual starting point for `groupby` and aggregation exercises.

```python
import pandas as pd
gapminder = pd.read_csv("data/gapminder.csv")
gapminder.head()
```

### Wide format (Software Carpentry python-novice-gapminder)

| File | Rows | Description |
| --- | --- | --- |
| `gapminder_all.csv` | 142 | All continents; GDP, life expectancy and population columns per year. |
| `gapminder_gdp_africa.csv` | 52 | GDP per capita per year, African countries. |
| `gapminder_gdp_americas.csv` | 25 | GDP per capita per year, the Americas. Also carries a leading `continent` column, as upstream does. |
| `gapminder_gdp_asia.csv` | 33 | GDP per capita per year, Asian countries. |
| `gapminder_gdp_europe.csv` | 30 | GDP per capita per year, European countries. |
| `gapminder_gdp_oceania.csv` | 2 | GDP per capita per year, Australia and New Zealand. |

One row per country, one column per year (`gdpPercap_1952` ... `gdpPercap_2007`).
These match the files used by the Software Carpentry lesson, so its episodes can
be taught unchanged.

```python
import pandas as pd
oceania = pd.read_csv("data/gapminder_gdp_oceania.csv", index_col="country")
oceania.loc["New Zealand"].plot()
```

### Sources

- Wide files: [swcarpentry/python-novice-gapminder](https://github.com/swcarpentry/python-novice-gapminder)
  `episodes/data/`, commit `5d886a81763f0c113f5560368311c44f41eea02d`.
- Tidy file: [swcarpentry/r-novice-gapminder](https://github.com/swcarpentry/r-novice-gapminder)
  `episodes/data/gapminder_data.csv`, commit `61dff93a6e329945d7c2a7520054e633c0ab3b62`.

Underlying data from [Gapminder](https://www.gapminder.org/data/), distributed
by the Carpentries under CC-BY 4.0.
