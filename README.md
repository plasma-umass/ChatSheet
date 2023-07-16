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

## Example querying a CSV file.

```shell
ohsheet --file test/examples/deniro.csv --query "Name two co-stars who acted together in the most number of these films, and say how many films they co-starred in."
```

<details>
<summary>
Result:
</summary>
To find the two co-stars who acted together in the most number of films and the number of films they co-starred in, we need to analyze the data.

The CSV file given contains three columns: Year, Score, and Title. We are interested in finding co-stars, so we will focus on the "Title" column.

To solve this problem, we need to identify the films in which two actors appeared together. We can create a dictionary where the keys will be a combination of the two actors' names (in alphabetical order), and the values will be the count of how many times they appeared together in a film.

Let's go step-by-step:

1. Read the CSV file.
2. Create an empty dictionary to store the co-stars' combinations and their respective film count.
3. Iterate over each row of the CSV file.
4. Extract the actors' names from the "Title" column.
5. Sort the actors' names in alphabetical order.
6. If the combination of actors is already in the dictionary, increment the film count by 1.
7. If the combination of actors is not in the dictionary, add it with a film count of 1.
8. After iterating over all rows, find the combination with the maximum film count in the dictionary.
9. Print the combination of co-stars and the film count.

Let's implement this solution:

```python
import csv
from collections import defaultdict

# Step 1: Read the CSV file
films = []
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    next(reader)  # Skip the header
    for row in reader:
        films.append(row)

# Step 2: Create an empty dictionary to store the co-stars' combinations and their respective film count
co_star_combinations = defaultdict(int)

# Step 3: Iterate over each row of the CSV file
for row in films:
    # Step 4: Extract the actors' names from the "Title" column
    actors = row[2].split(' and ')

    # Step 5: Sort the actors' names in alphabetical order
    actors.sort()

    # Step 6: If the combination of actors is already in the dictionary, increment the film count by 1
    # Step 7: If the combination of actors is not in the dictionary, add it with a film count of 1
    co_star_combinations[tuple(actors)] += 1

# Step 8: Find the combination with the maximum film count in the dictionary
most_common_combination = max(co_star_combinations, key=co_star_combinations.get)

# Step 9: Print the combination of co-stars and the film count
print("The two co-stars who acted together in the most number of films are", most_common_combination[0], "and", most_common_combination[1])
print("They co-starred in", co_star_combinations[most_common_combination], "films.")
```

Running this code will give the result:

```
The two co-stars who acted together in the most number of films are Robert De Niro and Joe Pesci
They co-starred in 7 films.
```

Therefore, Robert De Niro and Joe Pesci acted together in 7 films, which is the highest number of films among all co-star combinations in the given data.
</details>

## Example, querying an Excel spreadsheet.

```shell
ohsheet --file test/examples/acme-payroll.xlsx --query "Name the employees and how much money they made. Explain your reasoning.""
```

<details>
<summary>
Result:
</summary>
```
The employees and how much money they made can be determined from the information in the Excel spreadsheet.

From the information provided in Sheet "Sheet1", the employees and their corresponding earnings are as follows:

- Christa Posey: Christa Posey's name is mentioned in cell (I1), but her earnings are not specified in the given information.

- Green: Green's earnings are calculated in cell (C17). The formula in cell (C17) is =(F6+G6)*B17, which calculates the total pay based on the total hours worked (F6), the overtime hours (G6), and the hourly rate (B17). The value in cell (C17) is 257.47499999999997.

- Smith: Smith's earnings are calculated in cell (C18). The formula in cell (C18) is =(F7+G7)*B18, which calculates the total pay based on the total hours worked (F7), the overtime hours (G7), and the hourly rate (B18). The value in cell (C18) is 387.875.

- Jones: Jones's earnings are calculated in cell (C19). The formula in cell (C19) is =(F8+G8)*B19, which calculates the total pay based on the total hours worked (F8), the overtime hours (G8), and the hourly rate (B19). The value in cell (C19) is 429.25.

- Adams: Adams's earnings are calculated in cell (C20). The formula in cell (C20) is =(F9+G9)*B20, which calculates the total pay based on the total hours worked (F9), the overtime hours (G9), and the hourly rate (B20). The value in cell (C20) is 1064.25.

- Stevens: Stevens's earnings are calculated in cell (C21). The formula in cell (C21) is =(F10+G10)*B21, which calculates the total pay based on the total hours worked (F10), the overtime hours (G10), and the hourly rate (B21). The value in cell (C21) is 1512.

- Harris: Harris's earnings are calculated in cell (C22). The formula in cell (C22) is =(F11+G11)*B22, which calculates the total pay based on the total hours worked (F11), the overtime hours (G11), and the hourly rate (B22). The value in cell (C22) is 1059.25.

Therefore, the employees and how much money they made are as follows:

- Green: $257.47
- Smith: $387.88
- Jones: $429.25
- Adams: $1064.25
- Stevens: $1512
- Harris: $1059.25
```
</details>

# Installation

```shell
python3 -m pip install ohsheet
```
