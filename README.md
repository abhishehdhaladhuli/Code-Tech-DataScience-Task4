# CodeTech-DataScience-Task-4-Optimization-Model using LinearProgramming and pulp libraries in python 
COMPANY: CODETECH IT SOLUTIONS<br>
NAME: ABHISHEK DHALADHULI<br>
INTERN ID: CT6WVEQ<br>
DOMAIN: DATA SCIENCE<br>
DURATION:6 WEEKS<br>
MENTOR:NEELA SANTHOSH<br>
# 🚀 Maximizing Profit for a Manufacturing Company
This script is designed to solve a linear programming problem using the `PuLP` library in Python. Linear programming is a method to achieve the best outcome in a mathematical model whose requirements are represented by linear relationships. Here, the problem focuses on optimizing production to maximize profit given certain constraints on resources such as storage space and labor hours.

### Problem Statement:

The problem involves two products, Product X and Product Y, which a company can produce. Each product has associated profits, space requirements, and labor hours required for production. The objective is to maximize the total profit while ensuring that the production does not exceed the available storage space and labor hours.

### Code Explanation:

#### Importing Libraries:
```python
from pulp import LpProblem, LpMaximize, LpVariable, LpStatus
```
- `LpProblem`, `LpMaximize`, `LpVariable`, `LpStatus` are imported from the `PuLP` library.
- `LpProblem` is used to define the problem.
- `LpMaximize` indicates that the problem is a maximization problem.
- `LpVariable` is used to define decision variables.
- `LpStatus` is used to interpret the status of the solution.

#### Defining the Function:
```python
def optimize_production(profit_x, profit_y, space_x, space_y, total_space, labor_x, labor_y, total_labor):
```
- The function `optimize_production` takes dynamic inputs related to profits, space requirements, total available space, labor hours required, and total available labor hours for the two products.

#### Defining the Linear Programming Problem:
```python
model = LpProblem("Maximize_Profit", LpMaximize)
```
- `model` is an instance of `LpProblem` that defines the problem as "Maximize_Profit" with the objective to maximize (`LpMaximize`).

#### Defining Decision Variables:
```python
X = LpVariable("Product_X", lowBound=0, cat='Integer')
Y = LpVariable("Product_Y", lowBound=0, cat='Integer')
```
- `X` and `Y` are decision variables representing the number of units of Product X and Product Y to be produced.
- `lowBound=0` ensures that the variables cannot take negative values.
- `cat='Integer'` specifies that the variables are integers.

#### Defining the Objective Function:
```python
model += profit_x * X + profit_y * Y, "Total_Profit"
```
- The objective function is to maximize the total profit, which is the sum of profits from Product X and Product Y. This is added to the model.

#### Adding Constraints:
```python
model += space_x * X + space_y * Y <= total_space, "Storage_Constraint"
model += labor_x * X + labor_y * Y <= total_labor, "Labor_Constraint"
```
- Two constraints are added to the model:
  - Storage Constraint: The total space used by both products should not exceed the available storage space.
  - Labor Constraint: The total labor hours required for both products should not exceed the available labor hours.

#### Solving the Problem:
```python
model.solve()
```
- The `solve` method is called to solve the linear programming problem.

#### Extracting and Returning Results:
```python
result = {
    "status": LpStatus[model.status],
    "Product_X": int(X.varValue),
    "Product_Y": int(Y.varValue),
    "Maximum_Profit": int(model.objective.value())
}
    
return result
```
- The results are extracted and stored in a dictionary.
- `LpStatus[model.status]` gives the status of the solution (e.g., optimal, infeasible).
- `X.varValue` and `Y.varValue` give the optimal number of units for Product X and Product Y, respectively.
- `model.objective.value()` gives the maximum profit.

### Example Usage:
```python
if __name__ == "__main__":
    profit_x = int(input("Enter profit per unit for Product X: "))
    profit_y = int(input("Enter profit per unit for Product Y: "))
    space_x = int(input("Enter space required per unit for Product X: "))
    space_y = int(input("Enter space required per unit for Product Y: "))
    total_space = int(input("Enter total available storage space: "))
    labor_x = int(input("Enter labor hours required per unit for Product X: "))
    labor_y = int(input("Enter labor hours required per unit for Product Y: "))
    total_labor = int(input("Enter total available labor hours: "))

    result = optimize_production(profit_x, profit_y, space_x, space_y, total_space, labor_x, labor_y, total_labor)
    
    print("\nOptimization Results:")
    for key, value in result.items():
        print(f"{key}: {value}")
```
- The `if __name__ == "__main__":` block allows the script to be run as a standalone program.
- The user is prompted to enter the profits, space requirements, total available space, labor hours, and total available labor hours.
- The `optimize_production` function is called with these inputs, and the results are printed.

This code provides a flexible and efficient way to solve the production optimization problem using linear programming, helping the company to make informed decisions about the production quantities to maximize profit within given constraints.


