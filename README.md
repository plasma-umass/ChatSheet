# OhSheet

![OhSheet](https://upload.wikimedia.org/wikipedia/en/3/3d/Clay_Davis.jpg)

Instant data analysis for your CSV files or Excel spreadsheets.

# Usage

```shell
usage: ohsheet [-h] --file FILE --query QUERY

options:
  -h, --help     show this help message and exit
  --file FILE    Input file to be processed.
  --query QUERY  Query to be executed
```

# Examples

```shell
ohsheet --file test/examples/deniro.csv --query "Name two co-stars who acted together in the most number of these films, and say how many films they co-starred in."
ohsheet --file test/examples/acme-payroll.xlsx --query "Name the employees and how much money they made. Explain your reasoning.""
```

# Installation

```shell
python3 -m pip install ohsheet
```
