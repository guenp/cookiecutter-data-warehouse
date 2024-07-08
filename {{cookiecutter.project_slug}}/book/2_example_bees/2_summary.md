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

# Bees

This example shows how popular different plant species are with native and non-native bees alike.

```{code-cell}
:tags: [remove-cell]
import duckdb
con = duckdb.connect("my-data.duckdb")
```

```{code-cell}
:tags: [remove-input]
import plotly.express as px
fig = px.bar(con.sql("FROM top_plants").df(), x="plant_species", y="count_bee_species", color="is_bee_native", barmode="group")
fig
```