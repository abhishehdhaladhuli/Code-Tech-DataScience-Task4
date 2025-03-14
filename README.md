# CodeTech-DataScience-Task-1-Optimization-Model using LinearProgramming and pulp libraries in python 
COMPANY: CODETECH IT SOLUTIONS<br>
NAME: ABHISHEK DHALADHULI<br>
INTERN ID: CT6WVEQ<br>
DOMAIN: DATA SCIENCE<br>
DURATION:6 WEEKS<br>
MENTOR:NEELA SANTHOSH<br>
# 🚀 Maximizing Profit for a Manufacturing Company

## 📊 Problem Statement

A manufacturing company produces two products: **Product X** and **Product Y**. Each product contributes to the company's profit and requires specific amounts of storage space and labor hours.

The goal is to **maximize total profit** while considering the following **dynamic constraints** based on real-time inputs:

### ✅ Profit
- **Product X:** Generates a profit of ₹ *Pₓ* per unit.
- **Product Y:** Generates a profit of ₹ *Pᵧ* per unit.

### ✅ Storage Space
- **Product X:** Requires *Sₓ* units of storage space per unit.
- **Product Y:** Requires *Sᵧ* units of storage space per unit.
- **Total available storage space:** *Tₛ* units.

### ✅ Labor Hours
- **Product X:** Requires *Lₓ* labor hours per unit.
- **Product Y:** Requires *Lᵧ* labor hours per unit.
- **Total available labor hours:** *Tₗ* hours.

---

## 🎯 Objective

Formulate a **Linear Programming Model** to determine the optimal number of units of **Product X** and **Product Y** to produce in order to **maximize total profit**.

---

## 📈 Mathematical Model

### 🔢 Decision Variables
- \( X \): Number of units of Product X produced \( \geq 0 \)
- \( Y \): Number of units of Product Y produced \( \geq 0 \)

### 💸 Objective Function (Maximize Profit)
\[
\text{Maximize } Z = PₓX + PᵧY
\]

### 📏 Constraints
1. **Storage Constraint:**
\[
SₓX + SᵧY \leq Tₛ
\]
2. **Labor Constraint:**
\[
LₓX + LᵧY \leq Tₗ
\]
3. **Non-negativity Constraint:**
\[
X, Y \geq 0
\]

---


## 🔍 Explanation of the Code

Let’s break down the code step-by-step, explaining each part clearly:

### 📦 **1. Importing PuLP**
```python
from pulp import LpMaximize, LpProblem, LpVariable
```
- **`LpMaximize`**: Indicates the goal is to **maximize** the objective function (profit).
- **`LpProblem`**: Initializes the optimization problem with a name and a goal (maximize or minimize).
- **`LpVariable`**: Defines decision variables — the quantities of **Product X** and **Product Y** to produce.

### 🎯 **2. Defining the Optimization Problem**
```python
model = LpProblem(name='profit-maximization', sense=LpMaximize)
```
- **`name='profit-maximization'`**: A label for the problem — helpful when printing results.
- **`sense=LpMaximize`**: Sets the objective to **maximize** profit.

### 🔢 **3. Defining Decision Variables**
```python
X = LpVariable(name='Product_X', lowBound=0, cat='Integer')
Y = LpVariable(name='Product_Y', lowBound=0, cat='Integer')
```
- **`name`**: Identifies each variable clearly.
- **`lowBound=0`**: Ensures we don’t produce negative quantities.
- **`cat='Integer'`**: Restricts variables to whole numbers (because fractional units don’t make sense here).

### 📊 **4. Setting Dynamic Coefficients**
```python
P_x = float(input("Enter profit per unit of Product X: "))
P_y = float(input("Enter profit per unit of Product Y: "))
S_x = float(input("Enter storage required per unit of Product X: "))
S_y = float(input("Enter storage required per unit of Product Y: "))
T_s = float(input("Enter total available storage: "))
L_x = float(input("Enter labor hours required per unit of Product X: "))
L_y = float(input("Enter labor hours required per unit of Product Y: "))
T_l = float(input("Enter total available labor hours: "))
```
These coefficients are now dynamic, allowing user input for flexibility.

---



