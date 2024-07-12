---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Ducks

This example shows how to plot a ducky dataset (similar to the [Iris example](https://jupyterbook.org/en/stable/interactive/interactive.html#plotly)). The data is stored in DuckDB.

```{code-cell}
:tags: [remove-cell]
import duckdb
con = duckdb.connect("my-data.duckdb")
df = con.sql("FROM duck_iris").df()
```

```{code-cell}
:tags: [remove-input]
import plotly.io as pio
import plotly.express as px
import plotly.offline as py
from IPython.display import display

df = con.sql("FROM duck_iris").df()
fig = px.scatter(df, x="beak_length", y="tarsus_length", color="species", size="beak_width", width=700, height=500)
fig
```

```{code-cell}
:tags: [remove-input]
import plotly.io as pio
import plotly.express as px
import plotly.offline as py

fig = px.scatter_matrix(df, dimensions=["beak_width", "beak_length", "wing_length", "tail_length", "tarsus_length"], color="species", width=900, height=700)
fig.show()
```

```{code-cell}
:tags: [remove-input]
con.sql("""
SELECT
    COUNT(*) AS total_predictions,
    SUM(CASE WHEN y = y_pred THEN 1 ELSE 0 END) AS correct_predictions,
    CAST(SUM(CASE WHEN y = y_pred THEN 1 ELSE 0 END) AS FLOAT) / COUNT(*) AS accuracy
FROM predictions;
""").df()
```