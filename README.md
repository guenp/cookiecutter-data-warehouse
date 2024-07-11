<img src="logo.png" width=250>

# Cookiecutter Data Warehouse

This is a cookie cutter that helps you bootstrap a data warehouse for small data engineering and data science workloads. This will be presented at SciPy 2024 (see [How to bootstrap a Data Warehouse with DuckDB](https://cfp.scipy.org/2024/talk/review/PWR9M7BDFJDC7GXQYUXTCPG8Q8VE7EBL)).

## Install

1. Install `pipx` (see [docs](https://pipx.pypa.io/stable/installation/))

2. Install `cookiecutter`
```bash
pipx install cookiecutter
```

3. To create a new Data Warehouse project using this cookie cutter, run
```bash
pipx run cookiecutter gh:guenp/cookiecutter-data-warehouse
```

4. Browse into your newly created folder
```bash
cd <my_project_slug>
```

5. , create a new Python environment and install all Python requirements
```bash
python3 -m venv venv
./venv/bin/activate
pip install -r requirements.txt
```

6. Browse into the `/book` folder and build the Jupyter book
```bash
cd book
jupyter-book build .
```

7. Browse to the generated URL in the browser!


## How to use

To get started, take a look at the notebooks in the `example` project. To run and edit the notebooks, start a Jupyter Lab environment.

```bash
jupyter lab
```
