# Python for Data Science — Solved Question Papers (MCA)

**Darshan University — School of Computer Science / Darshan Institute of Computer Application**
**Course:** Python for Data Science (2105CS202 / 2305CS303) | **Marks:** 70 | **Duration:** 150 Minutes

This file contains the **original questions** (shown in blockquotes) from five papers, each followed by a **detailed, exam-oriented answer with examples**.

| Paper | Exam | Date |
|---|---|---|
| Paper 1 | MCA Sem-2, Summer-2022 (2105CS202) | 01.06.2022 |
| Paper 2 | MCA Sem-2, Summer-2023 (2105CS202) | 24-05-2023 |
| Paper 3 | MCA Sem-2, Winter-2023 (2105CS202) | 28-11-2023 |
| Paper 4 | MCA Sem-3, Winter-2024 (2305CS303) | 18-10-2024 |
| Paper 5 | MCA Sem-3, Winter-2025 (2305CS303) | 11-10-2025 |

**Instructions on each paper:** 1. Attempt all the questions. 2. Figures to the right indicate maximum marks. 3. Make suitable assumptions wherever necessary.

> **Note on repeated questions:** Many questions repeat across papers (e.g. NumPy conditional selection, join vs merge, Restaurant_order.csv, Titanic countplot/boxplot). The full answer is written at its first appearance; later appearances give a **short recap + a pointer** to the full answer so you can revise quickly.

---

## Common imports used in all programs

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

---

# PAPER 1 — MCA Sem-2 | Summer-2022 | 01.06.2022

---

## Q.1

### Q.1 (A) [4 Marks]
> List and explain steps of Data Science Pipeline.

**Definition:** A *Data Science Pipeline* is the end-to-end sequence of steps used to turn raw data into useful insights, predictions or decisions.

```
Problem Definition → Data Collection → Data Cleaning → EDA → Modeling → Evaluation → Deployment → Monitoring
```

| Step | Explanation | Example |
|---|---|---|
| 1. Problem Definition (Business Understanding) | Understand the goal, the question to answer and success metrics | "Predict which customers will leave the telecom company" |
| 2. Data Acquisition / Collection | Gather data from CSV, databases, APIs, web scraping, sensors | `pd.read_csv()`, SQL, BeautifulSoup |
| 3. Data Cleaning / Preparation (Wrangling) | Handle missing values, duplicates, outliers, wrong data types; encode categorical data; scale features | `df.dropna()`, `df.fillna()` |
| 4. Exploratory Data Analysis (EDA) | Summaries and visualizations to find patterns, correlations, anomalies | `df.describe()`, histograms, heatmaps |
| 5. Modeling | Select features and train ML algorithms | `LinearRegression().fit(X, y)` |
| 6. Evaluation | Measure performance with metrics on test data | accuracy, RMSE, confusion matrix |
| 7. Deployment & Communication | Put the model in production / present results with dashboards and reports | Flask API, Power BI |
| 8. Monitoring & Maintenance | Track performance, retrain with new data | Re-train monthly |

**Example (House-price prediction):** Define goal (predict price) → collect housing CSV → fill missing area values → plot price vs area → train Linear Regression → check R² → deploy as web app → monitor.

---

### Q.1 (B) [3 Marks]
> Explain %timeit command with example.
> **OR**
> Explain %run Command with example.

**%timeit (Magic command of IPython/Jupyter)**

`%timeit` measures the **execution time of a single statement** by running it many times (loops) and repeating that several times, then reporting the **mean ± standard deviation**. It automatically chooses the number of loops, so the result is reliable. Use `%%timeit` to time a whole cell.

**Syntax:** `%timeit [-n<N> -r<R>] statement`
- `-n` : number of loops per repeat
- `-r` : number of repeats
- `-o` : returns a TimeitResult object

**Example:**
```python
%timeit sum(range(1000))
# Output: 15.2 µs ± 120 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit -n 100 -r 5 [i**2 for i in range(1000)]
```
**Use:** compare two implementations (e.g. Python list loop vs NumPy vectorization) and choose the faster one.

**OR — %run command**

`%run` executes an **external Python script (.py) or notebook (.ipynb)** inside the current IPython session. After running, all variables/functions defined in the script become available in the current namespace.

**Example:** create `hello.py`
```python
# hello.py
x = 10
def greet(name):
    return "Hello " + name
print("Script executed")
```
Run in Jupyter:
```python
%run hello.py
# Output: Script executed
print(x)            # 10
print(greet("MCA")) # Hello MCA
```
**Options:** `%run -t script.py` (time it), `%run -i script.py` (run in current namespace), `%run -p script.py` (profile it), `%run script.py arg1 arg2` (command-line arguments via `sys.argv`).

---

### Q.1 (C) [7 Marks]
> What is NumPy? Explain arange, zeros, ones, eye, linspace, rand and randint functions with examples.
> **OR**
> Explain conditional selection with DataFrame with example.

**NumPy (Numerical Python)** is the fundamental open-source Python library for scientific computing. It provides the **ndarray** (N-dimensional array), fast vectorized mathematical operations, broadcasting, linear algebra, Fourier transforms and random number generation. NumPy arrays are **faster and more memory-efficient** than Python lists because they store homogeneous data in contiguous memory and are implemented in C.

```python
import numpy as np
```

| Function | Purpose | Example | Output |
|---|---|---|---|
| `np.arange(start, stop, step)` | Evenly spaced values (stop excluded) | `np.arange(0, 10, 2)` | `[0 2 4 6 8]` |
| `np.zeros(shape)` | Array filled with 0 | `np.zeros((2, 3))` | `[[0. 0. 0.] [0. 0. 0.]]` |
| `np.ones(shape)` | Array filled with 1 | `np.ones((2, 2))` | `[[1. 1.] [1. 1.]]` |
| `np.eye(n)` | Identity matrix (1 on diagonal) | `np.eye(3)` | `[[1. 0. 0.] [0. 1. 0.] [0. 0. 1.]]` |
| `np.linspace(start, stop, num)` | `num` evenly spaced points, stop **included** | `np.linspace(0, 1, 5)` | `[0. 0.25 0.5 0.75 1.]` |
| `np.random.rand(d0, d1)` | Random floats in [0, 1) uniform | `np.random.rand(2, 3)` | e.g. `[[0.12 0.85 0.43] [0.67 0.09 0.31]]` |
| `np.random.randint(low, high, size)` | Random integers in [low, high) | `np.random.randint(1, 10, 5)` | e.g. `[3 7 1 9 4]` |

**Program:**
```python
import numpy as np
print(np.arange(1, 11, 3))        # [ 1  4  7 10]
print(np.zeros((2, 2)))
print(np.ones((2, 3)))
print(np.eye(3))
print(np.linspace(0, 10, 5))      # [ 0.   2.5  5.   7.5 10. ]
print(np.random.rand(3))
print(np.random.randint(10, 50, size=(2, 3)))
```
**Difference arange vs linspace:** `arange` uses a *step*, `linspace` uses *number of points* and includes the end value.

**OR — Conditional selection with DataFrame**

Conditional (Boolean) selection filters rows of a DataFrame using a condition. The condition returns a Boolean Series (True/False), and passing it into `df[...]` keeps only rows where it is `True`.

```python
import pandas as pd
df = pd.DataFrame({
    'Name':  ['Amit', 'Riya', 'John', 'Sara', 'Kunal'],
    'Marks': [85, 55, 72, 90, 40],
    'City':  ['Rajkot', 'Surat', 'Rajkot', 'Vadodara', 'Surat']
})

print(df['Marks'] > 60)                    # Boolean Series
print(df[df['Marks'] > 60])                # rows with Marks > 60
print(df[(df['Marks'] > 60) & (df['City'] == 'Rajkot')])   # AND
print(df[(df['Marks'] < 50) | (df['Marks'] > 88)])         # OR
print(df[~(df['City'] == 'Surat')])                        # NOT
print(df[df['City'].isin(['Rajkot', 'Surat'])])            # isin
print(df.loc[df['Marks'] > 60, ['Name', 'Marks']])         # condition + column selection
print(df.query("Marks > 60 and City == 'Rajkot'"))         # query()
```
**Output of `df[df['Marks'] > 60]`:**
```
    Name  Marks      City
0   Amit     85    Rajkot
2   John     72    Rajkot
3   Sara     90  Vadodara
```
**Rules:** use `&`, `|`, `~` (not `and`, `or`, `not`) and wrap each condition in **parentheses**.

---

## Q.2

### Q.2 (A) [4 Marks]
> Compare Numpy and Pandas.

| Basis | NumPy | Pandas |
|---|---|---|
| Full form | Numerical Python | Panel Data / Python Data Analysis |
| Main data structure | `ndarray` (N-dimensional array) | `Series` (1-D) and `DataFrame` (2-D) |
| Data type | Homogeneous (single dtype) | Heterogeneous (different dtype per column) |
| Indexing | Integer position only | Labelled index (row & column labels) + position |
| Missing data | Poor support (`np.nan` only for float) | Excellent (`isnull`, `dropna`, `fillna`) |
| Best for | Numerical/mathematical computation, matrices, linear algebra | Data cleaning, analysis, tabular/CSV/Excel/SQL data |
| Speed / memory | Faster, lower memory | Slightly slower (more features) |
| File I/O | Limited (`loadtxt`) | Rich (`read_csv`, `read_excel`, `read_sql`, `read_json`) |
| Built on | C | NumPy |
| Example | `np.array([1,2,3])` | `pd.DataFrame({'a':[1,2]})` |

---

### Q.2 (B) [3 Marks]
> Explain join function in pandas with example.
> **OR**
> Explain merge function in pandas with example.

**`join()`** combines two DataFrames **based on their index** (by default a left join). It is a convenient shortcut for index-based merging.

**Syntax:** `df1.join(df2, on=None, how='left', lsuffix='', rsuffix='')`

```python
import pandas as pd
df1 = pd.DataFrame({'Name': ['A', 'B', 'C']}, index=[1, 2, 3])
df2 = pd.DataFrame({'Marks': [80, 90, 70]}, index=[1, 2, 4])

print(df1.join(df2))                 # left join (default)
#   Name  Marks
# 1    A   80.0
# 2    B   90.0
# 3    C    NaN

print(df1.join(df2, how='inner'))    # only common index 1, 2
print(df1.join(df2, how='outer'))    # all indexes 1, 2, 3, 4
```
`how` can be `left`, `right`, `inner`, `outer`. If both frames have a same column name use `lsuffix` / `rsuffix`.

**OR — `merge()`**

`pd.merge()` combines DataFrames using **one or more common columns (keys)** — similar to SQL JOIN.

**Syntax:** `pd.merge(left, right, on='key', how='inner', left_on=None, right_on=None)`

```python
emp = pd.DataFrame({'id': [1, 2, 3], 'name': ['Amit', 'Riya', 'John']})
sal = pd.DataFrame({'id': [1, 2, 4], 'salary': [30000, 40000, 50000]})

print(pd.merge(emp, sal, on='id'))                 # inner (default)
#    id  name  salary
# 0   1  Amit   30000
# 1   2  Riya   40000

print(pd.merge(emp, sal, on='id', how='left'))     # all from emp
print(pd.merge(emp, sal, on='id', how='right'))    # all from sal
print(pd.merge(emp, sal, on='id', how='outer'))    # all rows
```
| how | Result |
|---|---|
| inner | only matching keys |
| left | all left rows + matching right |
| right | all right rows + matching left |
| outer | all rows from both |

---

### Q.2 (C) [7 Marks]
> Explain NetworkX library with example.
> **OR**
> Explain different types of graphs available in seaborn.

**NetworkX** is a Python library for the **creation, manipulation and study of complex networks (graphs)** — nodes (vertices) connected by edges (links). It supports undirected `Graph`, directed `DiGraph`, `MultiGraph`, and `MultiDiGraph`. Applications: social networks, road maps, computer networks, recommendation systems.

**Installation:** `pip install networkx`

**Main features:** add/remove nodes and edges, node/edge attributes, graph algorithms (shortest path, degree, connected components, centrality), and drawing with Matplotlib.

**Example:**
```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()                       # undirected graph
G.add_node("A")
G.add_nodes_from(["B", "C", "D"])
G.add_edge("A", "B")
G.add_edges_from([("B", "C"), ("C", "D"), ("D", "A")])

print("Nodes :", G.nodes())          # ['A', 'B', 'C', 'D']
print("Edges :", G.edges())          # [('A','B'), ('A','D'), ('B','C'), ('C','D')]
print("Degree:", dict(G.degree()))   # {'A': 2, 'B': 2, 'C': 2, 'D': 2}
print("Shortest path A->C:", nx.shortest_path(G, "A", "C"))

nx.draw(G, with_labels=True, node_color="lightblue", node_size=800, font_weight="bold")
plt.show()
```
**Directed graph:** `D = nx.DiGraph(); D.add_edge("A","B")` — edges have direction (A→B).
**Weighted edge:** `G.add_edge("A","B", weight=5)`.

**OR — Types of graphs (plots) in Seaborn**

Seaborn is a statistical visualization library built on Matplotlib. Its plots are grouped by purpose:

| Category | Functions | Purpose |
|---|---|---|
| Relational | `scatterplot`, `lineplot`, `relplot` | Relationship between two numeric variables |
| Distribution | `histplot`, `kdeplot`, `displot`, `rugplot`, `ecdfplot` | Distribution of one (or two) variables |
| Categorical | `barplot`, `countplot`, `boxplot`, `violinplot`, `stripplot`, `swarmplot`, `pointplot`, `catplot` | Numeric vs categorical comparison |
| Regression | `regplot`, `lmplot` | Scatter + fitted regression line |
| Matrix | `heatmap`, `clustermap` | Colour-coded matrix / correlation |
| Multi-plot grids | `pairplot`, `jointplot`, `FacetGrid` | Many plots at once |

```python
import seaborn as sns
tips = sns.load_dataset("tips")
sns.scatterplot(x="total_bill", y="tip", data=tips)
sns.histplot(tips["total_bill"], kde=True)
sns.boxplot(x="day", y="total_bill", data=tips)
sns.countplot(x="day", data=tips)
sns.heatmap(tips.corr(numeric_only=True), annot=True, cmap="coolwarm")
sns.pairplot(tips)
```

---

## Q.3

### Q.3 (A) [4 Marks]
> Explain Multi-Index DataFrame in pandas with example.

A **MultiIndex (hierarchical index)** DataFrame has **two or more levels of index** on rows (or columns). It lets you represent higher-dimensional data in a 2-D table and select data at multiple levels.

**Creating:**
```python
import pandas as pd
index = pd.MultiIndex.from_tuples(
    [('2023', 'Q1'), ('2023', 'Q2'), ('2024', 'Q1'), ('2024', 'Q2')],
    names=['Year', 'Quarter'])
df = pd.DataFrame({'Sales': [100, 150, 120, 180]}, index=index)
print(df)
#                Sales
# Year Quarter
# 2023 Q1          100
#      Q2          150
# 2024 Q1          120
#      Q2          180
```
**Other ways:** `pd.MultiIndex.from_product([['A','B'],[1,2]])`, `df.set_index(['col1','col2'])`.

**Selection:**
```python
df.loc['2023']                  # all rows of 2023
df.loc[('2023', 'Q2')]          # single row
df.xs('Q1', level='Quarter')    # cross-section by inner level
df.unstack()                    # inner level -> columns
df.groupby(level='Year').sum()  # aggregate on one level
```
**Advantages:** compact representation, easy group-wise analysis, works with `xs()`, `unstack()`, `stack()`.

---

### Q.3 (B) [3 Marks]
> Explain Axes, Ticks and Grid in Matplotlib with example.
> **OR**
> Explain Labels, Annotation and Legends in Matplotlib.

- **Axes:** the actual plotting area (the x-axis and y-axis with the data) inside a Figure. A Figure can have many Axes (subplots). Created by `fig, ax = plt.subplots()`.
- **Ticks:** the small marks on an axis showing scale values; **tick labels** are the text at those marks. Controlled with `set_xticks()`, `set_xticklabels()`, `tick_params()`.
- **Grid:** background lines aligned with ticks that make values easy to read; `ax.grid(True)`.

```python
import matplotlib.pyplot as plt
import numpy as np
x = np.arange(1, 6)
y = x ** 2

fig, ax = plt.subplots()
ax.plot(x, y, marker='o')
ax.set_xticks([1, 2, 3, 4, 5])                         # tick positions
ax.set_xticklabels(['A', 'B', 'C', 'D', 'E'])          # tick labels
ax.tick_params(axis='both', direction='in', length=6, labelcolor='blue')
ax.set_xlim(0, 6); ax.set_ylim(0, 30)                  # axes limits
ax.grid(True, linestyle='--', color='gray', alpha=0.6) # grid
plt.show()
```

**OR — Labels, Annotation and Legends**

- **Labels:** text that names the axes and plot: `plt.xlabel('X')`, `plt.ylabel('Y')`, `plt.title('Title')`.
- **Annotation:** text with an optional arrow pointing at a specific data point: `plt.annotate(text, xy, xytext, arrowprops)`.
- **Legend:** a key explaining each line/marker; requires `label=` in each plot call, then `plt.legend(loc='upper left')`.

```python
x = [1, 2, 3, 4]
y1 = [1, 4, 9, 16]
y2 = [2, 4, 6, 8]
plt.plot(x, y1, 'r-o', label='Square')
plt.plot(x, y2, 'b--s', label='Double')
plt.xlabel('Input'); plt.ylabel('Output'); plt.title('Labels, Annotation & Legend')
plt.annotate('Max point', xy=(4, 16), xytext=(2.5, 14),
             arrowprops=dict(facecolor='black', arrowstyle='->'))
plt.legend(loc='upper left')
plt.show()
```

---

### Q.3 (C) [7 Marks]
> Write a python program that performs following tasks using NumPy
> 1) Create NumPy array of 200 random integer numbers from 1 to 200.
> 2) Display the standard deviation.
> 3) Display the sum of all the elements.
> 4) Display all the elements which are less than 10 from array.
> 5) Display only odd elements from array.
> 6) Reshape the array into 4 * 50.
> 7) Display the sum of all Columns.

```python
import numpy as np

# 1) 200 random integers from 1 to 200 (high is exclusive, so use 201)
arr = np.random.randint(1, 201, size=200)
print("Array:", arr)

# 2) Standard deviation
print("Standard Deviation:", np.std(arr))          # or arr.std()

# 3) Sum of all elements
print("Sum:", np.sum(arr))                         # or arr.sum()

# 4) Elements less than 10
print("Elements < 10:", arr[arr < 10])

# 5) Only odd elements
print("Odd elements:", arr[arr % 2 != 0])

# 6) Reshape to 4 x 50
reshaped = arr.reshape(4, 50)
print("Shape:", reshaped.shape)                    # (4, 50)

# 7) Sum of all columns (axis=0 -> down each column; gives 50 values)
print("Column sums:", reshaped.sum(axis=0))
```
**Explanation:** `randint(1, 201)` generates values 1–200. Boolean masking `arr[arr < 10]` selects elements by condition. `reshape(4, 50)` needs 4×50 = 200 elements. `axis=0` sums columns, `axis=1` would sum rows.

**OR — Restaurant_order.csv tasks**

Columns: `order_id, quantity, item_name, choice_description, item_price`

```python
import pandas as pd

# 1) Import dataset into 'rsorder'
url = 'http://abc.com/Restaurant_order.csv'
rsorder = pd.read_csv(url)            # add sep='\t' if file is tab separated

# 2) Names of all columns
print(rsorder.columns)                # or list(rsorder.columns)

# 3) Number of rows
print(rsorder.shape[0])               # or len(rsorder)

# 4) Most-ordered item (by total quantity)
most_item = rsorder.groupby('item_name')['quantity'].sum().idxmax()
print(most_item)

# 5) How many of the most-ordered item were ordered
total = rsorder.groupby('item_name')['quantity'].sum().max()
print(total)

# 6) Lambda function to change type of item_price (e.g. "$2.39" -> 2.39)
rsorder['item_price'] = rsorder['item_price'].apply(lambda x: float(str(x).replace('$', '')))
print(rsorder['item_price'].dtype)    # float64

# 7) Revenue for the period
revenue = (rsorder['quantity'] * rsorder['item_price']).sum()
print("Revenue:", revenue)
```
**Note:** `item_price` is read as text like `$2.39`; the lambda removes `$` and converts to float so that arithmetic is possible.

---

## Q.4

### Q.4 (A) [4 Marks]
> Write a Pandas program to drop the columns where at least one element is missing in a given DataFrame.
> ```
>    Rollno  Enrollment  Name
> 0     101        1111   NaN
> 1     102        1122   NaN
> 2     103        1133   xyz
> ```

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'Rollno':     [101, 102, 103],
    'Enrollment': [1111, 1122, 1133],
    'Name':       [np.nan, np.nan, 'xyz']
})
print("Original DataFrame:\n", df)

# axis=1 -> drop columns ; how='any' (default) -> drop if at least one NaN
result = df.dropna(axis=1, how='any')
print("\nAfter dropping columns with missing values:\n", result)
```
**Output:**
```
   Rollno  Enrollment
0     101        1111
1     102        1122
2     103        1133
```
The `Name` column has NaN in two rows so it is removed. (`how='all'` would drop only columns in which *all* values are NaN.)

---

### Q.4 (B) [3 Marks]
> Discuss the Classes available in Scikit-learn library.
> **OR**
> Compare Supervised and Unsupervised learning.

**Scikit-learn (sklearn)** is Python's main machine-learning library built on NumPy, SciPy and Matplotlib. Its API is consistent: **Estimator** (`fit()`), **Predictor** (`predict()`), **Transformer** (`transform()`).

| Module / Classes | Examples |
|---|---|
| Classification | `LogisticRegression`, `KNeighborsClassifier`, `DecisionTreeClassifier`, `RandomForestClassifier`, `SVC`, `GaussianNB` |
| Regression | `LinearRegression`, `Ridge`, `Lasso`, `DecisionTreeRegressor`, `SVR` |
| Clustering | `KMeans`, `DBSCAN`, `AgglomerativeClustering` |
| Dimensionality reduction | `PCA`, `TruncatedSVD` |
| Preprocessing | `StandardScaler`, `MinMaxScaler`, `LabelEncoder`, `OneHotEncoder` |
| Model selection | `train_test_split`, `cross_val_score`, `GridSearchCV` |
| Metrics | `accuracy_score`, `confusion_matrix`, `mean_squared_error`, `r2_score` |
| Feature extraction | `CountVectorizer`, `TfidfVectorizer` |
| Datasets | `load_iris`, `load_digits`, `make_blobs` |
| Pipeline | `Pipeline`, `make_pipeline` |

**OR — Supervised vs Unsupervised Learning**

| Basis | Supervised | Unsupervised |
|---|---|---|
| Data | Labelled (input + known output) | Unlabelled (only input) |
| Goal | Predict output for new data | Discover hidden structure/patterns |
| Feedback | Yes (errors compared with labels) | No |
| Tasks | Classification, Regression | Clustering, Association, Dimensionality reduction |
| Algorithms | Linear/Logistic Regression, KNN, SVM, Decision Tree | K-Means, Hierarchical, PCA, Apriori |
| Accuracy | Can be measured directly | Harder to evaluate |
| Example | Spam / not spam email | Grouping customers by behaviour |

---

### Q.4 (C) [7 Marks]
> What is clustering? Explore K-mean on sample data (random X and Y values) to create 3 clusters and print center of each cluster.
> **OR**
> What is Exploratory Data Analysis (EDA)? Explain it with titanic datasets

**Clustering** is an **unsupervised learning** technique that groups similar data points into clusters so that points in the same cluster are more similar to each other than to those in other clusters. **K-Means** is a centroid-based algorithm:
1. Choose K (number of clusters) and initialise K centroids.
2. Assign every point to the nearest centroid (Euclidean distance).
3. Recompute each centroid as the mean of its assigned points.
4. Repeat steps 2–3 until the centroids stop changing.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

np.random.seed(42)
X = np.random.randint(1, 100, 50)       # random X values
Y = np.random.randint(1, 100, 50)       # random Y values
data = np.column_stack((X, Y))

kmeans = KMeans(n_clusters=3, random_state=42, n_init=10)
kmeans.fit(data)

print("Cluster centers:\n", kmeans.cluster_centers_)   # centre of each cluster
print("Labels:", kmeans.labels_)

plt.scatter(X, Y, c=kmeans.labels_, cmap='viridis')
plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1],
            c='red', marker='X', s=200, label='Centroids')
plt.legend(); plt.title('K-Means (K=3)'); plt.show()
```
**Output (sample):** three rows such as `[[22.4, 75.1], [78.3, 24.6], [70.9, 78.2]]` (values depend on random data).

**OR — Exploratory Data Analysis (EDA)**

**EDA** is the process of examining a dataset using summary statistics and visualizations to understand its structure, find patterns, detect outliers/missing values and test assumptions **before** modelling.

**EDA on Titanic dataset:**
```python
import seaborn as sns
import matplotlib.pyplot as plt
df = sns.load_dataset('titanic')

df.head()                      # first look
df.shape                       # (891, 15)
df.info()                      # dtypes and non-null counts
df.describe()                  # mean, std, min, max
df.isnull().sum()              # missing values (age, deck, embarked)

df['age'] = df['age'].fillna(df['age'].median())    # handle missing values

sns.countplot(x='survived', data=df)                 # how many survived
sns.countplot(x='sex', hue='survived', data=df)      # females survived more
sns.boxplot(x='pclass', y='age', data=df)            # age by class
sns.histplot(df['age'], kde=True)                    # age distribution
sns.heatmap(df.select_dtypes('number').corr(), annot=True)   # correlation
df.groupby('sex')['survived'].mean()                 # female ~0.74, male ~0.19
```
**Typical findings:** women and 1st-class passengers had higher survival rates; `age` and `deck` have missing values; `fare` is right-skewed with outliers.

---

## Q.5

### Q.5 (A) [4 Marks]
> Explain TF-IDF with example.

**TF-IDF (Term Frequency–Inverse Document Frequency)** is a text-vectorization technique that gives each word a weight showing how **important it is in a document relative to the whole collection (corpus)**. Common words (the, is) get low weight; rare, informative words get high weight.

- **TF(t, d)** = (number of times term t appears in d) / (total terms in d)
- **IDF(t)** = log (N / number of documents containing t)  (N = total documents)
- **TF-IDF = TF × IDF**

**Example:** D1 = "the cat sat", D2 = "the dog sat", D3 = "the cat ran" (N = 3, log base 10)

| Term | TF in D1 | Docs containing | IDF = log(3/df) | TF-IDF in D1 |
|---|---|---|---|---|
| the | 1/3 | 3 | log(3/3) = 0 | 0 |
| cat | 1/3 | 2 | log(3/2) = 0.176 | 0.0587 |
| sat | 1/3 | 2 | 0.176 | 0.0587 |

"the" gets weight 0 (appears everywhere); "cat" and "sat" get a positive weight.

```python
from sklearn.feature_extraction.text import TfidfVectorizer
docs = ["the cat sat", "the dog sat", "the cat ran"]
tfidf = TfidfVectorizer()
X = tfidf.fit_transform(docs)
print(tfidf.get_feature_names_out())   # ['cat' 'dog' 'ran' 'sat' 'the']
print(X.toarray().round(2))
```

---

### Q.5 (B) [3 Marks]
> Explain Generalization, Overfitting, and Underfitting.
> **OR**
> Explain the confusion matrix with an example.

- **Generalization:** the ability of a model to perform well on **new, unseen data**, not just training data. The goal of machine learning is good generalization.
- **Overfitting:** the model is **too complex** and memorises training data including noise → **very high training accuracy but low test accuracy** (high variance). Causes: too many features, deep trees, too little data. Fixes: more data, simpler model, regularization, cross-validation, pruning.
- **Underfitting:** the model is **too simple** to capture the pattern → **low accuracy on both training and test data** (high bias). Fixes: more complex model, add features, train longer.

| | Training accuracy | Test accuracy |
|---|---|---|
| Underfitting | Low | Low |
| Good fit | High | High (close to training) |
| Overfitting | Very high | Low |

**OR — Confusion Matrix**

A **confusion matrix** is a table that summarises the performance of a **classification** model by comparing actual and predicted classes.

|  | Predicted Positive | Predicted Negative |
|---|---|---|
| **Actual Positive** | TP (True Positive) | FN (False Negative) |
| **Actual Negative** | FP (False Positive) | TN (True Negative) |

**Example:** TP = 50, FN = 10, FP = 5, TN = 35 (total 100)
- Accuracy = (TP+TN)/Total = 85/100 = **0.85**
- Precision = TP/(TP+FP) = 50/55 = **0.91**
- Recall = TP/(TP+FN) = 50/60 = **0.83**
- F1-score = 2·P·R/(P+R) = **0.87**

```python
from sklearn.metrics import confusion_matrix
y_true = [1, 0, 1, 1, 0, 1, 0, 0]
y_pred = [1, 0, 1, 0, 0, 1, 1, 0]
print(confusion_matrix(y_true, y_pred))
# [[3 1]
#  [1 3]]
```

---

### Q.5 (C) [7 Marks]
> What is Linear Regression? Write a python program to predict future price of iPhone. Consider Columns of CSV file as follow. `iphoneNumber, model_name, price`
> **OR**
> What is Classification? Write a python program to classify iris flowers. Use K-nearest Neighbors algorithm for classification. For training of model use inbuild iris dataset available in sklearn.

**Linear Regression** is a supervised learning algorithm that models the relationship between a dependent variable (y) and one or more independent variables (X) by fitting a straight line: **y = m·x + c** (m = slope/coefficient, c = intercept). It minimises the sum of squared errors (Least Squares).

**Program — predict future iPhone price** (`iphoneNumber` = generation number such as 6, 7, 8 … used as X; `price` = y):
```python
import pandas as pd
import numpy as np
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score
import matplotlib.pyplot as plt

df = pd.read_csv('iphone.csv')           # columns: iphoneNumber, model_name, price
X = df[['iphoneNumber']]                 # independent variable (2-D)
y = df['price']                          # dependent variable

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1)

model = LinearRegression()
model.fit(X_train, y_train)

print("Slope     :", model.coef_[0])
print("Intercept :", model.intercept_)
print("R2 score  :", r2_score(y_test, model.predict(X_test)))

# Predict price of a future model, e.g. iPhone 16
future = pd.DataFrame({'iphoneNumber': [16]})
print("Predicted price of iPhone 16:", model.predict(future)[0])

plt.scatter(X, y, color='blue')
plt.plot(X, model.predict(X), color='red')
plt.xlabel('iPhone Number'); plt.ylabel('Price'); plt.title('iPhone Price Prediction')
plt.show()
```

**OR — Classification** is a supervised learning task in which the model predicts a **discrete class label** for a new input (e.g. spam/not spam, iris species).

**K-Nearest Neighbours (KNN):** to classify a new point, find the K closest training points (Euclidean distance) and assign the class that is most common among them (majority vote).

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, confusion_matrix

iris = load_iris()
X, y = iris.data, iris.target

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)
y_pred = knn.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
print(confusion_matrix(y_test, y_pred))

# classify a new flower: sepal length, sepal width, petal length, petal width
sample = [[5.1, 3.5, 1.4, 0.2]]
print("Predicted species:", iris.target_names[knn.predict(sample)[0]])   # setosa
```

---

# PAPER 2 — MCA Sem-2 | Summer-2023 | 24-05-2023

---

## Q.1

### Q.1 (A) [4 Marks]
> Explain different coding styles available in python programming.

Python is a **multi-paradigm** language; the common coding styles (programming paradigms) are:

| Style | Idea | Example |
|---|---|---|
| **Imperative** | Gives step-by-step instructions that change program state using statements, loops, assignments | `total = 0` / `for i in range(1,6): total += i` |
| **Procedural** | Imperative code organised into reusable procedures/functions | `def add(a,b): return a+b` |
| **Functional** | Computation by evaluating pure functions; uses `map`, `filter`, `reduce`, `lambda`, comprehensions; avoids changing state | `list(map(lambda x: x*x, [1,2,3]))` |
| **Object-Oriented (OOP)** | Data and methods are bundled in classes/objects; uses encapsulation, inheritance, polymorphism | `class Student: ...` |

```python
nums = [1, 2, 3, 4, 5]

# Imperative
total = 0
for n in nums:
    total += n

# Functional
from functools import reduce
total_f = reduce(lambda a, b: a + b, nums)      # 15
squares = [n**2 for n in nums if n % 2 == 0]    # [4, 16]

# Object-oriented
class Calculator:
    def add(self, a, b):
        return a + b
print(Calculator().add(2, 3))                   # 5
```
Data science typically mixes functional (pandas/NumPy vectorized operations) with imperative and OOP (scikit-learn estimators).

---

### Q.1 (B) [3 Marks]
> Explain different factors that control the speed of execution for data science application.
> **OR**
> Explain the differences between conda and pip.

**Factors controlling speed of execution:**
1. **Algorithm & time complexity** — an O(n log n) algorithm beats O(n²) on large data.
2. **Choice of data structure** — set/dict lookups are O(1); list search is O(n).
3. **Vectorization** — NumPy/pandas vectorized operations run in compiled C and are far faster than Python `for` loops.
4. **Hardware** — CPU speed/cores, RAM size, SSD vs HDD, GPU for deep learning.
5. **Memory usage / data types** — using `float32` or `category` dtype reduces memory and speeds up processing.
6. **I/O operations** — reading big CSV files, database or network calls are slow; use chunking, binary formats (Parquet).
7. **Parallelism & concurrency** — `multiprocessing`, `joblib`, Dask; the Python GIL limits threads for CPU-bound tasks.
8. **Compiled/optimised libraries** — Numba, Cython, PyPy, JIT compilation.
9. **Code quality** — avoiding repeated computations, caching (`functools.lru_cache`), profiling with `%timeit`.

**OR — conda vs pip**

| Basis | conda | pip |
|---|---|---|
| Full form | Cross-platform package and *environment* manager (Anaconda/Miniconda) | "Pip Installs Packages" — Python package installer |
| Languages | Any language (Python, R, C libraries) | Python packages only |
| Source | Anaconda repository / conda-forge | PyPI (Python Package Index) |
| Environments | Built-in (`conda create -n env`) | Needs `venv`/`virtualenv` |
| Dependency solving | Full dependency resolver incl. non-Python libs | Basic resolver, Python only |
| Package format | Pre-compiled binaries | Wheels / source |
| Install | `conda install numpy` | `pip install numpy` |
| Python version management | Yes | No |

---

### Q.1 (C) [7 Marks]
> List and explain any seven magic commands with an example.
> **OR**
> Explain python ecosystem for data science.

**Magic commands** are special commands of IPython/Jupyter, prefixed with `%` (**line magic**, works on one line) or `%%` (**cell magic**, works on the entire cell). They provide shortcuts for common tasks.

| # | Command | Purpose | Example |
|---|---|---|---|
| 1 | `%lsmagic` | List all available magic commands | `%lsmagic` |
| 2 | `%pwd` | Show current working directory | `%pwd` → `'C:\\Users\\student'` |
| 3 | `%run` | Run an external Python script | `%run hello.py` |
| 4 | `%time` | Time a statement/cell (single run) | `%time sum(range(10**6))` → `Wall time: 25 ms` |
| 5 | `%timeit` | Time a statement over many runs (mean ± std) | `%timeit sum(range(1000))` |
| 6 | `%who` / `%whos` | List variables in the namespace (`%whos` gives details) | `%who` → `a b df x` |
| 7 | `%matplotlib inline` | Display plots inside the notebook | `%matplotlib inline` |
| bonus | `%reset` | Delete all variables | `%reset -f` |
| bonus | `%history` | Show command history | `%history -n` |
| bonus | `%%writefile` | Write cell content to a file | `%%writefile test.py` |
| bonus | `%load` | Load code from a file into the cell | `%load test.py` |

```python
%lsmagic
%pwd
x = 10; y = 20
%who                     # x   y
%timeit [i*i for i in range(1000)]
%matplotlib inline
import matplotlib.pyplot as plt
plt.plot([1, 2, 3]); plt.show()
```

**OR — Python ecosystem for data science**

| Area | Libraries / Tools | Role |
|---|---|---|
| Core language | Python 3 | General-purpose, easy syntax |
| Numerical computing | **NumPy**, **SciPy** | Arrays, linear algebra, statistics, optimisation |
| Data manipulation | **Pandas** | Series/DataFrame, cleaning, grouping, merging |
| Visualisation | **Matplotlib**, **Seaborn**, Plotly, Bokeh | Charts and interactive graphs |
| Machine learning | **scikit-learn**, XGBoost, LightGBM | Classification, regression, clustering |
| Deep learning | TensorFlow, Keras, PyTorch | Neural networks |
| Statistics | statsmodels | Statistical tests, time-series models |
| NLP | NLTK, spaCy | Text processing |
| Web scraping | **Beautiful Soup**, Scrapy, Requests | Collecting web data |
| Graph/network | **NetworkX** | Graph analysis |
| Environment/IDE | **Jupyter Notebook**, Anaconda, Spyder, VS Code | Interactive development |
| Package managers | pip, conda | Install libraries |
| Big data | PySpark, Dask | Large-scale processing |

Python dominates data science because of its simplicity, huge library ecosystem, strong community and integration with databases, web and ML tools.

---

## Q.2

### Q.2 (A) [4 Marks]
> Explain web scrapping using beautiful Soap.

**Web scraping** is the automated extraction of data from websites. **Beautiful Soup (bs4)** is a Python library that **parses HTML/XML** and creates a parse tree so that tags, attributes and text can be searched easily. It is normally used with the `requests` library, which downloads the page.

**Install:** `pip install beautifulsoup4 requests lxml`

**Steps:** 1) Send HTTP request → 2) Get HTML → 3) Create `BeautifulSoup` object → 4) Find elements → 5) Extract text/attributes → 6) Store (CSV/DataFrame).

```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")

print(soup.title.text)                       # page title
print(soup.find("h1").text)                  # first <h1>
for p in soup.find_all("p"):                 # all paragraphs
    print(p.get_text())
for a in soup.find_all("a", href=True):      # all links
    print(a["href"])
print(soup.select("div.content > p"))        # CSS selector
```
**Common methods:** `find()`, `find_all()`, `select()`, `get_text()`, `.attrs`, `.parent`, `.children`.

---

### Q.2 (B) [3 Marks]
> Explain conditional selection in a numpy array.
> **OR**
> Explain rand(), randint(), randn() functions of numpy with example.

**Conditional selection (Boolean masking):** applying a condition to an array gives a Boolean array; using it as an index returns only the elements where the condition is `True`.

```python
import numpy as np
arr = np.array([5, 12, 8, 21, 3, 16])

mask = arr > 10
print(mask)              # [False  True False  True False  True]
print(arr[mask])         # [12 21 16]
print(arr[arr % 2 == 0]) # [12  8 16]       even numbers
print(arr[(arr > 5) & (arr < 20)])          # [12  8 16]  (use & | ~ with parentheses)
arr[arr < 5] = 0                            # modify selected elements -> [ 5 12  8 21  0 16]
print(np.where(arr > 10, 1, 0))             # [0 1 0 1 0 1]
```

**OR — rand(), randint(), randn()**

| Function | Description | Example |
|---|---|---|
| `np.random.rand(d0, d1, …)` | Random floats from **uniform** distribution in [0, 1) | `np.random.rand(3)` → `[0.37 0.95 0.73]` |
| `np.random.randint(low, high, size)` | Random **integers** in [low, high) | `np.random.randint(1, 100, 5)` → `[45 12 78 3 66]` |
| `np.random.randn(d0, d1, …)` | Random floats from **standard normal** distribution (mean 0, std 1); can be negative | `np.random.randn(2, 2)` → `[[ 0.5 -1.2] [ 0.1 0.8]]` |

```python
np.random.seed(1)                # reproducible results
print(np.random.rand(2, 2))
print(np.random.randint(10, 20, size=(2, 3)))
print(np.random.randn(3))
```

---

### Q.2 (C) [7 Marks]
> Explain numpy array creation functions with example.
> **OR**
> Explain cross sections in DataFrame with example.

NumPy provides several functions to create arrays:

| Function | Description | Example → Output |
|---|---|---|
| `np.array(list)` | From list/tuple | `np.array([1,2,3])` → `[1 2 3]` |
| `np.zeros(shape)` | All zeros | `np.zeros((2,2))` → `[[0. 0.] [0. 0.]]` |
| `np.ones(shape)` | All ones | `np.ones(3)` → `[1. 1. 1.]` |
| `np.full(shape, v)` | Filled with value `v` | `np.full((2,2), 7)` → `[[7 7] [7 7]]` |
| `np.empty(shape)` | Uninitialised (random garbage) | `np.empty(2)` |
| `np.eye(n)` / `np.identity(n)` | Identity matrix | `np.eye(2)` → `[[1. 0.] [0. 1.]]` |
| `np.diag(list)` | Diagonal matrix | `np.diag([1,2])` → `[[1 0] [0 2]]` |
| `np.arange(start, stop, step)` | Range with step | `np.arange(0,10,3)` → `[0 3 6 9]` |
| `np.linspace(start, stop, n)` | n equally spaced values (stop included) | `np.linspace(0,1,3)` → `[0. 0.5 1.]` |
| `np.random.rand / randint / randn` | Random arrays | `np.random.randint(1,5,3)` |
| `np.zeros_like(a)`, `np.ones_like(a)` | Same shape as `a` | `np.zeros_like(arr)` |

```python
import numpy as np
a = np.array([[1, 2, 3], [4, 5, 6]])
print(a.shape, a.ndim, a.dtype)          # (2, 3) 2 int64
print(np.zeros((2, 3)))
print(np.full((2, 2), 9))
print(np.eye(3))
print(np.arange(1, 10, 2))               # [1 3 5 7 9]
print(np.linspace(0, 100, 5))            # [  0.  25.  50.  75. 100.]
```

**OR — Cross sections in DataFrame (`xs()`)**

The **`xs()`** method returns a **cross-section** (a slice of rows or columns) of a DataFrame, mainly useful with a **MultiIndex** where you want to select by a particular index level without specifying the other levels.

**Syntax:** `df.xs(key, axis=0, level=None, drop_level=True)`

```python
import pandas as pd
idx = pd.MultiIndex.from_tuples(
    [('A', 'x'), ('A', 'y'), ('B', 'x'), ('B', 'y')], names=['Group', 'Type'])
df = pd.DataFrame({'Value': [10, 20, 30, 40]}, index=idx)

print(df.xs('A'))                         # all rows where Group = 'A'
#       Value
# Type
# x        10
# y        20

print(df.xs('x', level='Type'))           # all rows where Type = 'x' (across groups)
#         Value
# Group
# A          10
# B          30

print(df.xs(('B', 'y')))                  # single row  -> Value 40
print(df.xs('Value', axis=1))             # cross-section of a column
```
`xs()` is shorter than `.loc` with `pd.IndexSlice` when selecting on an inner level.

---

## Q.3

### Q.3 (A) [4 Marks]
> Explain time series with example.

A **time series** is a sequence of data points recorded at **successive, usually equally spaced, time intervals** (daily temperature, stock price, monthly sales). Pandas has strong support through `DatetimeIndex`, `Timestamp`, `date_range`, `resample`, `shift` and `rolling`.

```python
import pandas as pd
import numpy as np

dates = pd.date_range(start='2023-01-01', periods=6, freq='D')   # daily dates
ts = pd.Series([10, 12, 9, 15, 14, 18], index=dates)
print(ts)
# 2023-01-01    10
# 2023-01-02    12 ...

print(ts['2023-01-03'])                     # select by date -> 9
print(ts['2023-01-02':'2023-01-04'])        # slicing by date range
print(ts.resample('2D').mean())             # resample to 2-day averages
print(ts.rolling(window=3).mean())          # 3-day moving average
print(ts.shift(1))                          # lag by 1 day
print(ts.pct_change())                      # daily percentage change

df = pd.DataFrame({'date': dates, 'sales': ts.values})
df['date'] = pd.to_datetime(df['date'])
df = df.set_index('date')
df['month'] = df.index.month                # extract date parts
ts.plot(title='Time Series')                # visualise
```
**Components of a time series:** Trend, Seasonality, Cyclic pattern, Irregular/Noise.

---

### Q.3 (B) [3 Marks]
> Differentiate pandas vs numpy.
> **OR**
> Differentiate join and merge.

**Pandas vs NumPy:** see the full table in **Paper 1 → Q.2 (A)**. Summary: NumPy = homogeneous N-dimensional arrays for fast numerical computation; Pandas = labelled, heterogeneous tabular data (Series/DataFrame, built on NumPy) for data cleaning and analysis, with rich file I/O and missing-data handling.

**OR — join vs merge**

| Basis | `join()` | `merge()` |
|---|---|---|
| Called as | DataFrame method: `df1.join(df2)` | Function `pd.merge(df1, df2)` or method `df1.merge(df2)` |
| Joins on | **Index** (by default); can use `on=` for the caller's column | **Columns** (keys) via `on`, `left_on`, `right_on`; can also use index |
| Default `how` | `left` | `inner` |
| Flexibility | Less flexible, simple | More flexible, SQL-like |
| Same column names | Needs `lsuffix`/`rsuffix` | Automatic `_x`, `_y` suffixes (customisable) |
| Example | `df1.join(df2, how='inner')` | `pd.merge(df1, df2, on='id', how='outer')` |

(`join` is internally a wrapper over `merge`.) Examples are in **Paper 1 → Q.2 (B)**.

---

### Q.3 (C) [7 Marks]
> Consider following Restaurant_order.csv: `order_id, quantity, item_name, choice_description, item_price`
> Using pandas perform the following tasks.
> 1) Import the dataset from 'http://abc.com/ Restaurant_order.csv' and assign it to a variable called 'rsorder'
> 2) What is the number of observations in the dataset?
> 3) Which was the most-ordered item?
> 4) For the most-ordered item, how many items were ordered?
> 5) What was the most ordered item in the choice_description column?
> 6) How many items were ordered in total?
> 7) How many different items are sold?

```python
import pandas as pd

# 1) Import dataset
rsorder = pd.read_csv('http://abc.com/Restaurant_order.csv')

# 2) Number of observations (rows)
print(rsorder.shape[0])              # or len(rsorder)

# 3) Most-ordered item (by total quantity)
item_qty = rsorder.groupby('item_name')['quantity'].sum()
print(item_qty.idxmax())

# 4) How many of the most-ordered item were ordered
print(item_qty.max())

# 5) Most ordered item in choice_description column
print(rsorder['choice_description'].value_counts().idxmax())
# (value_counts().head(1) shows it with its count)

# 6) Total items ordered
print(rsorder['quantity'].sum())

# 7) Number of different items sold
print(rsorder['item_name'].nunique())      # or len(rsorder['item_name'].unique())
```
**Key functions:** `shape`, `groupby().sum()`, `idxmax()`, `value_counts()`, `sum()`, `nunique()`.

**OR — Salaries.csv** (`Id, EmployeeName, JobTitle, BasePay, TotalPay, Year`)
> 1) Read Salaries.csv as a dataframe called 'sal'. 2) Display first 25 entries of dataframe. 3) What is the average BasePay? 4) What job title does an "XYZ" employee hold? 5) What is the name of highest paid person? 6) What was the average (mean) BasePay of all employees per year? (2011-2014)? 7) How many Job Titles were represented by only one person in 2013?

```python
import pandas as pd

# 1) Read file
sal = pd.read_csv('Salaries.csv')

# 2) First 25 entries
print(sal.head(25))

# 3) Average BasePay
print(sal['BasePay'].mean())

# 4) Job title of employee "XYZ"
print(sal[sal['EmployeeName'] == 'XYZ']['JobTitle'])
#   (or) sal.loc[sal['EmployeeName'] == 'XYZ', 'JobTitle']

# 5) Name of highest-paid person (by TotalPay)
print(sal.loc[sal['TotalPay'].idxmax(), 'EmployeeName'])

# 6) Mean BasePay per year (2011-2014)
print(sal.groupby('Year')['BasePay'].mean())

# 7) Job titles held by only one person in 2013
counts = sal[sal['Year'] == 2013]['JobTitle'].value_counts()
print(sum(counts == 1))
```

---

## Q.4

### Q.4 (A) [4 Marks]
> Explain label, annotation and legend in matplotlib.

- **Label:** text that identifies axes and the chart — `plt.xlabel()`, `plt.ylabel()`, `plt.title()`; also `label=` inside `plot()` names a data series.
- **Annotation:** adds explanatory text, optionally with an arrow, at a particular data point — `plt.annotate(text, xy=(point), xytext=(text position), arrowprops=dict(...))`.
- **Legend:** a box that explains what each line/marker/colour represents — requires `label=`, shown by `plt.legend(loc='best')`. Parameters: `loc`, `fontsize`, `title`, `ncol`, `frameon`.

```python
import matplotlib.pyplot as plt
months = ['Jan', 'Feb', 'Mar', 'Apr']
a = [10, 25, 18, 30]
b = [8, 15, 20, 22]
plt.plot(months, a, 'g-o', label='Product A')
plt.plot(months, b, 'r--s', label='Product B')
plt.xlabel('Month'); plt.ylabel('Sales'); plt.title('Monthly Sales')
plt.annotate('Peak sales', xy=('Apr', 30), xytext=('Feb', 29),
             arrowprops=dict(arrowstyle='->', color='black'))
plt.legend(loc='upper left')
plt.grid(True)
plt.show()
```

---

### Q.4 (B) [3 Marks]
> Explain choropleth graph with an example.
> **OR**
> Explain Networkx library with an undirection graph.

A **choropleth map** is a thematic map in which **geographic regions (countries, states, districts) are shaded/coloured in proportion to a data value** (population density, GDP, election results). Darker shade = higher value. It is created with Plotly, Folium or GeoPandas.

```python
import plotly.express as px
import pandas as pd

df = pd.DataFrame({
    'state': ['Gujarat', 'Maharashtra', 'Rajasthan', 'Kerala'],
    'literacy': [78, 82, 66, 94]
})
# Using a built-in world dataset (country level)
df_w = px.data.gapminder().query("year == 2007")
fig = px.choropleth(df_w, locations="iso_alpha", color="lifeExp",
                    hover_name="country", color_continuous_scale="Viridis",
                    title="Life Expectancy 2007")
fig.show()
```
(For Indian states, `px.choropleth(df, geojson=india_geojson, locations='state', featureidkey='properties.ST_NM', color='literacy')`.)

**OR — NetworkX with an undirected graph**

An **undirected graph** (`nx.Graph`) has edges with **no direction** — an edge A–B means A is connected to B and B to A (e.g. friendship, road between cities).

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_edges_from([("Rajkot", "Ahmedabad"), ("Ahmedabad", "Surat"),
                  ("Surat", "Mumbai"), ("Rajkot", "Surat")])

print(G.nodes())
print(G.edges())
print("Neighbours of Surat:", list(G.neighbors("Surat")))
print("Degree:", dict(G.degree()))
print("Is connected:", nx.is_connected(G))
print("Path:", nx.shortest_path(G, "Rajkot", "Mumbai"))

nx.draw(G, with_labels=True, node_color='lightgreen', node_size=1500)
plt.show()
```
More about NetworkX: **Paper 1 → Q.2 (C)**.

---

### Q.4 (C) [7 Marks]
> Write a python program read following marksheet.csv file and implement a heatmap on subject marks also handle missing data. `Roll No., Name, DS, PDS, SE, WT, PSC`
> **OR**
> Write a python program to implement countplot and boxplot with titanic dataset.

A **heatmap** displays a matrix as colours; here the subject marks of every student (rows) are colour-coded.

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# 1) Read the file
df = pd.read_csv('marksheet.csv')
print(df.head())
print("Missing values:\n", df.isnull().sum())

# 2) Handle missing data
subjects = ['DS', 'PDS', 'SE', 'WT', 'PSC']
df[subjects] = df[subjects].apply(pd.to_numeric, errors='coerce')   # bad text -> NaN
df[subjects] = df[subjects].fillna(df[subjects].mean())             # fill with subject mean
df = df.dropna(subset=['Roll No.', 'Name'])                         # drop rows missing id/name
# (alternative: df.dropna() to delete incomplete rows)

# 3) Heatmap of subject marks (students x subjects)
plt.figure(figsize=(8, 6))
sns.heatmap(df[subjects].set_index(df['Name']), annot=True, cmap='YlGnBu',
            linewidths=0.5, fmt='.0f')
plt.title('Subject-wise Marks Heatmap')
plt.xlabel('Subjects'); plt.ylabel('Students')
plt.show()

# (optional) correlation between subjects
sns.heatmap(df[subjects].corr(), annot=True, cmap='coolwarm')
plt.show()
```

**OR — countplot and boxplot with Titanic**
```python
import seaborn as sns
import matplotlib.pyplot as plt

titanic = sns.load_dataset('titanic')          # or pd.read_csv('titanic.csv')

# Countplot -> number of observations in each category
plt.figure(figsize=(6, 4))
sns.countplot(x='sex', hue='survived', data=titanic, palette='Set2')
plt.title('Survival count by Sex')
plt.show()

# Boxplot -> distribution (median, quartiles, outliers) of a numeric variable
plt.figure(figsize=(6, 4))
sns.boxplot(x='pclass', y='age', data=titanic, palette='Set3')
plt.title('Age distribution by Passenger Class')
plt.show()
```
- **Countplot:** bar chart of counts of a categorical variable (only x needed).
- **Boxplot:** shows minimum, Q1, median, Q3, maximum and outliers (points beyond 1.5×IQR).

---

## Q.5

### Q.5 (A) [4 Marks]
> What is hashing trick? Explain countvectorizer with an example.

**Hashing trick (feature hashing):** a technique for converting text tokens into a **fixed-length numeric vector** by applying a **hash function** to each word and using the hash value (mod vector size) as the column index. No vocabulary dictionary needs to be stored, so it is **memory-efficient and fast** for very large datasets; the drawback is possible *hash collisions* (two words map to the same index). Implemented as `HashingVectorizer(n_features=16)`.

**CountVectorizer** (scikit-learn) converts a collection of text documents to a **matrix of token counts** (Bag-of-Words). It builds a vocabulary of all unique words and counts how many times each appears in each document.

```python
from sklearn.feature_extraction.text import CountVectorizer, HashingVectorizer

docs = ["I love python", "I love data science", "python is fun"]
cv = CountVectorizer()
X = cv.fit_transform(docs)

print(cv.get_feature_names_out())
# ['data' 'fun' 'is' 'love' 'python' 'science']   (note: single-letter "I" is ignored by default)
print(X.toarray())
# [[0 0 0 1 1 0]
#  [1 0 0 1 0 1]
#  [0 1 1 0 1 0]]

hv = HashingVectorizer(n_features=8)      # hashing trick
print(hv.transform(docs).toarray().shape) # (3, 8)
```

---

### Q.5 (B) [3 Marks]
> Explain bag of words model.
> **OR**
> Explain generalization, overfitting, and underfitting.

The **Bag of Words (BoW)** model represents a text document as an **unordered collection (bag) of its words**, ignoring grammar and word order but keeping the **frequency** of each word. Steps: (1) collect all documents (corpus), (2) tokenise and build a vocabulary of unique words, (3) represent each document as a vector of word counts.

**Example:** S1 = "I like pizza", S2 = "I like pasta"; vocabulary = [I, like, pizza, pasta]
- S1 → [1, 1, 1, 0]
- S2 → [1, 1, 0, 1]

**Advantages:** simple, easy to implement. **Disadvantages:** loses word order and meaning, large sparse vectors, common words dominate (fixed by TF-IDF/stop-word removal).
```python
from sklearn.feature_extraction.text import CountVectorizer
print(CountVectorizer(lowercase=True, token_pattern=r"(?u)\b\w+\b").fit_transform(["I like pizza","I like pasta"]).toarray())
```

**OR — Generalization, Overfitting, Underfitting:** see the complete answer in **Paper 1 → Q.5 (B)**. In short — *Generalization* = performing well on unseen data; *Overfitting* = memorising training data (high train accuracy, low test accuracy, high variance); *Underfitting* = model too simple (poor train & test accuracy, high bias).

---

### Q.5 (C) [7 Marks]
> What is regression? Explain linear regression with an example.
> **OR**
> What is classification? Explain k-Nearest neighbours with an example.

**Regression** is a **supervised learning** technique used to predict a **continuous numeric value** (price, temperature, salary) from one or more input variables.

**Linear regression** fits a straight line **y = m·x + c** between the input X and output y by minimising the sum of squared residuals (least-squares). Multiple linear regression: y = b0 + b1x1 + b2x2 + …. Metrics: MSE, RMSE, R².

**Example:** predict salary from years of experience.
```python
import numpy as np
from sklearn.linear_model import LinearRegression

X = np.array([[1], [2], [3], [4], [5]])             # experience (years)
y = np.array([30000, 35000, 40000, 45000, 50000])   # salary

model = LinearRegression()
model.fit(X, y)
print("Slope m     :", model.coef_[0])      # 5000.0
print("Intercept c :", model.intercept_)    # 25000.0
print("Salary for 6 years:", model.predict([[6]])[0])   # 55000.0
print("R2:", model.score(X, y))             # 1.0
```
Equation: **salary = 5000 × experience + 25000** → for 6 years = 55,000.

**OR — Classification** is a supervised learning task that predicts a **categorical class label** (spam/not spam, species). **k-Nearest Neighbours (kNN)** is a simple, lazy, distance-based algorithm: for a new point, find the **k closest training points** (Euclidean distance) and assign the **majority class** among them.

**Example:**
```python
from sklearn.neighbors import KNeighborsClassifier
# [height, weight] -> 0 = Normal, 1 = Overweight
X = [[150, 50], [160, 55], [170, 90], [180, 100], [155, 52], [175, 95]]
y = [0, 0, 1, 1, 0, 1]

knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X, y)
print(knn.predict([[165, 85]]))    # [1]  -> Overweight (majority of 3 nearest)
```
Steps: choose k → compute distance → pick k nearest → vote. Small k = noisy/overfit, large k = smooth/underfit. Iris-dataset version: **Paper 1 → Q.5 (C) OR**.

---

# PAPER 3 — MCA Sem-2 | Winter-2023 | 28-11-2023

---

## Q.1

### Q.1 (A) [4 Marks]
> Explain data science pipeline in detail.

The **Data Science Pipeline** is the ordered workflow that converts raw data into actionable insight. (Full table with examples: **Paper 1 → Q.1 (A)**.) Detailed explanation:

1. **Problem definition / Business understanding** — decide the question, objective, and success metric (e.g. reduce customer churn by 10%).
2. **Data collection (acquisition)** — from files (CSV, Excel, JSON), databases (SQL/MySQL), web scraping (Beautiful Soup), APIs, sensors/logs.
3. **Data cleaning & preparation (wrangling)** — handle missing values (`fillna`, `dropna`), remove duplicates, fix data types, treat outliers, encode categories, scale/normalise features, feature engineering.
4. **Exploratory Data Analysis (EDA)** — descriptive statistics, histograms, box plots, correlation heatmaps to discover patterns.
5. **Modelling** — split data (train/test), select algorithm (regression, classification, clustering), train with `fit()`.
6. **Evaluation** — accuracy, precision, recall, F1, RMSE, R²; cross-validation; tune hyper-parameters.
7. **Deployment & visualisation/communication** — deploy as API/app, dashboards, reports for stakeholders.
8. **Monitoring & maintenance** — detect model drift, retrain with new data.

```
Define → Collect → Clean → Explore → Model → Evaluate → Deploy → Monitor
   ▲___________________________ iterate / feedback __________________________|
```
The pipeline is **iterative** — results of evaluation often send us back to cleaning or feature engineering.

---

### Q.1 (B) [3 Marks]
> Explain python's role in data science.
> **OR**
> Explain functional and imperative coding styles in python.

**Role of Python in data science:**
- **Simple, readable syntax** — easy for statisticians, analysts and beginners.
- **Rich library ecosystem** — NumPy, Pandas, SciPy (computing); Matplotlib, Seaborn (visualisation); scikit-learn, TensorFlow, PyTorch (ML/DL); NLTK, spaCy (NLP); Beautiful Soup (scraping).
- **Covers the whole pipeline** — collection, cleaning, analysis, modelling, visualisation, deployment.
- **Interactive tools** — Jupyter Notebook, Anaconda, Google Colab.
- **Integration** — connects to SQL/NoSQL databases, Hadoop/Spark, web APIs, C/C++ code.
- **Large community, open source, free, cross-platform.**
- **Scalability** — works for small scripts up to big-data (PySpark, Dask).

**OR — Functional vs Imperative style**

| Basis | Imperative | Functional |
|---|---|---|
| Idea | Describes **how** to do it using statements that change state | Describes **what** to compute using pure functions |
| State | Mutable variables | Avoids mutation; immutable data |
| Control flow | Loops (`for`, `while`), `if` | Recursion, `map`, `filter`, `reduce`, comprehensions, `lambda` |
| Side effects | Common | Avoided |
| Readability | Step by step | Concise |

```python
nums = [1, 2, 3, 4, 5, 6]

# Imperative: sum of squares of even numbers
result = 0
for n in nums:
    if n % 2 == 0:
        result += n * n
print(result)          # 56

# Functional: same task
from functools import reduce
result_f = reduce(lambda a, b: a + b, map(lambda x: x*x, filter(lambda x: x % 2 == 0, nums)))
print(result_f)        # 56
```

---

### Q.1 (C) [7 Marks]
> Explain python ecosystem for data science.
> **OR**
> Explain %run, %time, %timeit and %reset magic commands with example.

**Python ecosystem for data science:** the complete collection of libraries and tools around Python used for data tasks — NumPy/SciPy (numerical), Pandas (data frames), Matplotlib/Seaborn/Plotly (visualisation), scikit-learn/XGBoost (machine learning), TensorFlow/Keras/PyTorch (deep learning), statsmodels (statistics), NLTK/spaCy (NLP), Beautiful Soup/Scrapy/Requests (scraping), NetworkX (graphs), Jupyter/Anaconda/Spyder (environments), pip/conda (package managers), PySpark/Dask (big data). The detailed table is in **Paper 2 → Q.1 (C) OR**.

**OR — Magic commands**

| Command | Meaning | Example |
|---|---|---|
| `%run` | Runs an external `.py`/`.ipynb` file; its variables/functions come into the session | `%run hello.py` |
| `%time` | Times **one execution** of a statement (CPU time & wall time) | `%time sum(range(10**6))` → `Wall time: 30.1 ms` |
| `%timeit` | Runs statement **many times** and reports mean ± std — more accurate | `%timeit sum(range(1000))` → `14.9 µs ± 100 ns per loop` |
| `%reset` | **Deletes all variables/names** from the namespace; `-f` skips confirmation | `%reset -f` |

```python
x = 5; y = 10
%who                    # x  y
%reset -f               # clear everything
%who                    # Interactive namespace is empty.

%run hello.py           # executes script
%time total = sum(i*i for i in range(100000))
%timeit total = sum(i*i for i in range(100000))
```
`%time` = single run (can vary), `%timeit` = repeated runs (better benchmark). Cell versions: `%%time`, `%%timeit`.

---

## Q.2

### Q.2 (A) [4 Marks]
> Explain database connectively with MySQL database with a simple example.

Python connects to MySQL with a driver such as **mysql-connector-python** (`pip install mysql-connector-python`) or PyMySQL. The **DB-API** steps are: connect → create cursor → execute SQL → fetch/commit → close.

```python
import mysql.connector

# 1) Connect to MySQL server
conn = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="college"
)
cursor = conn.cursor()                        # 2) create cursor

# 3) Create table & insert
cursor.execute("CREATE TABLE IF NOT EXISTS student(id INT PRIMARY KEY, name VARCHAR(50), marks INT)")
cursor.execute("INSERT INTO student VALUES (%s, %s, %s)", (1, "Amit", 85))
cursor.executemany("INSERT INTO student VALUES (%s, %s, %s)", [(2, "Riya", 90), (3, "John", 70)])
conn.commit()                                 # save changes (needed for INSERT/UPDATE/DELETE)

# 4) Fetch data
cursor.execute("SELECT * FROM student")
for row in cursor.fetchall():                 # fetchone(), fetchmany(n) also available
    print(row)                                # (1, 'Amit', 85) ...

# 5) Close
cursor.close()
conn.close()
```
**Read directly into Pandas:** `pd.read_sql("SELECT * FROM student", conn)`. Always use **parameterised queries** (`%s`) to prevent SQL injection.

---

### Q.2 (B) [3 Marks]
> Explain sort() function of numpy with an example.
> **OR**
> Explain conditional selection in a numpy array.

`np.sort(a, axis=-1, kind='quicksort')` returns a **sorted copy** of the array (ascending). `a.sort()` sorts **in place**. `axis` selects the direction: `axis=0` sorts each column, `axis=1` (default, last) sorts each row. `np.argsort()` returns the sorted **indices**. Descending order: `np.sort(a)[::-1]`.

```python
import numpy as np
a = np.array([30, 10, 50, 20, 40])
print(np.sort(a))              # [10 20 30 40 50]
print(np.sort(a)[::-1])        # [50 40 30 20 10]
print(np.argsort(a))           # [1 3 0 4 2]

m = np.array([[9, 3, 6], [4, 8, 1]])
print(np.sort(m, axis=1))      # sort each row    -> [[3 6 9] [1 4 8]]
print(np.sort(m, axis=0))      # sort each column -> [[4 3 1] [9 8 6]]

a.sort()                       # in-place
print(a)
```

**OR — Conditional selection in a numpy array:** see the full answer in **Paper 2 → Q.2 (B)**. Summary: a condition such as `arr > 10` creates a Boolean mask; `arr[arr > 10]` selects matching elements; combine conditions with `&`, `|`, `~` inside parentheses; `np.where(cond, x, y)` chooses values element-wise.
```python
arr = np.array([5, 12, 8, 21, 3, 16])
print(arr[arr > 10])           # [12 21 16]
print(arr[(arr > 5) & (arr < 20)])   # [12  8 16]
```

---

### Q.2 (C) [7 Marks]
> Explain arange(), zeros(), ones(), eye() and linspace() functions with example.
> **OR**
> Explain xs() and groupby() functions of pandas with example.

```python
import numpy as np
```
| Function | Syntax | Example | Output |
|---|---|---|---|
| `arange()` | `np.arange(start, stop, step)` — evenly spaced values, **stop excluded** | `np.arange(2, 12, 3)` | `[ 2  5  8 11]` |
| `zeros()` | `np.zeros(shape, dtype)` — filled with 0 (default float) | `np.zeros((2, 3))` | `[[0. 0. 0.] [0. 0. 0.]]` |
| `ones()` | `np.ones(shape)` — filled with 1 | `np.ones((2, 2), dtype=int)` | `[[1 1] [1 1]]` |
| `eye()` | `np.eye(N, M=None, k=0)` — 1 on the diagonal (identity matrix); `k` shifts diagonal | `np.eye(3)` | `[[1. 0. 0.] [0. 1. 0.] [0. 0. 1.]]` |
| `linspace()` | `np.linspace(start, stop, num)` — `num` equally spaced points, **stop included** | `np.linspace(0, 1, 5)` | `[0. 0.25 0.5 0.75 1.]` |

```python
print(np.arange(10))                 # [0 1 2 3 4 5 6 7 8 9]
print(np.arange(1, 2, 0.25))         # [1.   1.25 1.5  1.75]
print(np.zeros(4))                   # [0. 0. 0. 0.]
print(np.eye(3, k=1))                # ones on the upper diagonal
print(np.linspace(10, 20, 3))        # [10. 15. 20.]
```
**Difference:** `arange` = fixed *step size*; `linspace` = fixed *number of points*.

**OR — `xs()` and `groupby()` in pandas**

**`xs()`** returns a cross-section of a (Multi-Index) DataFrame by key and level (details in **Paper 2 → Q.2 (C) OR**).

**`groupby()`** implements **split → apply → combine**: it splits data into groups by one or more keys, applies an aggregation (`sum`, `mean`, `count`, `max`, `agg`) and combines the results.

```python
import pandas as pd
df = pd.DataFrame({
    'Dept':   ['IT', 'HR', 'IT', 'HR', 'Finance'],
    'Name':   ['A', 'B', 'C', 'D', 'E'],
    'Salary': [50000, 40000, 60000, 45000, 55000]
})

print(df.groupby('Dept')['Salary'].mean())
# Dept
# Finance    55000.0
# HR         42500.0
# IT         55000.0

print(df.groupby('Dept')['Salary'].agg(['min', 'max', 'sum']))
print(df.groupby('Dept').size())                 # number of rows per group

# xs() with MultiIndex created by groupby on two keys
g = df.groupby(['Dept', 'Name'])['Salary'].sum()
print(g.xs('IT', level='Dept'))                  # only IT rows
print(g.xs('B', level='Name'))                   # name B in any dept
```

---

## Q.3

### Q.3 (A) [4 Marks]
> Explain conditional selection on DataFrame.

Conditional (Boolean) selection filters DataFrame rows using conditions. A condition produces a Boolean Series; `df[condition]` returns only the `True` rows. Full example with `&`, `|`, `~`, `isin`, `loc`, `query`: **Paper 1 → Q.1 (C) OR**. Quick example:

```python
import pandas as pd
df = pd.DataFrame({'Name': ['Amit', 'Riya', 'John', 'Sara'],
                   'Marks': [85, 55, 72, 90],
                   'City': ['Rajkot', 'Surat', 'Rajkot', 'Vadodara']})

print(df[df['Marks'] > 60])                                  # single condition
print(df[(df['Marks'] > 60) & (df['City'] == 'Rajkot')])     # AND  -> Amit, John
print(df[(df['Marks'] < 60) | (df['City'] == 'Vadodara')])   # OR   -> Riya, Sara
print(df[df['City'].isin(['Surat', 'Vadodara'])])            # isin
print(df.loc[df['Marks'] > 60, ['Name']])                    # condition + column pick
```
Remember: use `&`, `|`, `~` with parentheses; `and`/`or`/`not` cause errors with Series.

---

### Q.3 (B) [3 Marks]
> Differentiate join and merge.
> **OR**
> Explain multi-index DataFrame with an example.

**join vs merge:** full comparison table in **Paper 2 → Q.3 (B) OR**.

| Basis | `join()` | `merge()` |
|---|---|---|
| Joins on | Index (default) | Columns/keys (`on`, `left_on`, `right_on`) |
| Default `how` | left | inner |
| Flexibility | Less | More (SQL style) |
| Syntax | `df1.join(df2)` | `pd.merge(df1, df2, on='id')` |

**OR — Multi-Index DataFrame:** a DataFrame with **hierarchical (two or more level) index**. Full explanation: **Paper 1 → Q.3 (A)**. Example:
```python
import pandas as pd
idx = pd.MultiIndex.from_product([['2023', '2024'], ['Q1', 'Q2']], names=['Year', 'Quarter'])
df = pd.DataFrame({'Sales': [100, 150, 120, 180]}, index=idx)
print(df.loc['2023'])                  # select outer level
print(df.xs('Q1', level='Quarter'))    # select inner level
print(df.unstack())                    # inner level -> columns
```

---

### Q.3 (C) [7 Marks]
> Consider following Restaurant_order.csv `order_id, quantity, item_name, choice_description, item_price`
> 1) Import the dataset from 'http://abc.com/restaurant_order.csv' and assign it to a variable called 'rsorder'
> 2) Display first 25 entries of DataFrame.
> 3) How is the dataset indexed?
> 4) What is the number of observations in the dataset?
> 5) Which was the most-ordered item?
> 6) What was the most ordered item in the choice_description column?
> 7) How many items were ordered in total?

```python
import pandas as pd

# 1) Import
rsorder = pd.read_csv('http://abc.com/restaurant_order.csv')

# 2) First 25 entries
print(rsorder.head(25))

# 3) How is the dataset indexed?  (default RangeIndex 0..n-1)
print(rsorder.index)               # RangeIndex(start=0, stop=4622, step=1)

# 4) Number of observations
print(rsorder.shape[0])            # or len(rsorder)

# 5) Most-ordered item
item_qty = rsorder.groupby('item_name')['quantity'].sum()
print(item_qty.idxmax())

# 6) Most ordered value in choice_description
print(rsorder['choice_description'].value_counts().idxmax())

# 7) Total items ordered
print(rsorder['quantity'].sum())
```
The dataset is indexed by the default integer `RangeIndex`; a different column can be made the index with `rsorder.set_index('order_id')`.

**OR — Salaries.csv** (`Id, EmployeeName, JobTitle, BasePay, TotalPay, Year`)
> 1) Read Salaries.csv as a DataFrame called 'sal'. 2) Display last 25 entries of DataFrame. 3) What is the average BasePay? 4) Print the name of all the columns. 5) What job title does an "XYZ" employee hold? 6) What is the name of highest paid person? 7) Summarize the DataFrame.

```python
import pandas as pd

sal = pd.read_csv('Salaries.csv')                              # 1
print(sal.tail(25))                                            # 2) last 25 entries
print(sal['BasePay'].mean())                                   # 3) average BasePay
print(sal.columns)                                             # 4) all column names
print(sal[sal['EmployeeName'] == 'XYZ']['JobTitle'])           # 5) job title of "XYZ"
print(sal.loc[sal['TotalPay'].idxmax(), 'EmployeeName'])       # 6) highest paid person
sal.info()                                                     # 7) summary: dtypes, non-null counts
print(sal.describe())                                          #    statistical summary
```

---

## Q.4

### Q.4 (A) [4 Marks]
> Explain different types of line appearances available in matplotlib.

In Matplotlib the appearance of a line is controlled through **line style, width, colour, markers, transparency** etc. — as arguments of `plt.plot()` or as a *format string* like `'r--o'`.

| Property | Parameter | Values / Examples |
|---|---|---|
| Line style | `linestyle` / `ls` | `'-'` solid, `'--'` dashed, `':'` dotted, `'-.'` dash-dot |
| Line width | `linewidth` / `lw` | `lw=3` |
| Colour | `color` / `c` | `'red'`, `'r'`, `'#FF5733'`, `(0.1,0.2,0.5)` |
| Marker | `marker` | `'o'` circle, `'s'` square, `'^'` triangle, `'*'` star, `'+'`, `'x'`, `'D'` |
| Marker size/colour | `markersize` / `ms`, `markerfacecolor`, `markeredgecolor` | `ms=8` |
| Transparency | `alpha` | 0 (transparent) to 1 (opaque) |
| Label | `label` | for legend |
| Draw order | `zorder` | |

```python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4]
plt.plot(x, [1, 2, 3, 4],  linestyle='-',  color='red',    linewidth=2, marker='o', label='solid')
plt.plot(x, [2, 3, 4, 5],  linestyle='--', color='blue',   linewidth=2, marker='s', label='dashed')
plt.plot(x, [3, 4, 5, 6],  linestyle=':',  color='green',  linewidth=3, marker='^', label='dotted')
plt.plot(x, [4, 5, 6, 7],  linestyle='-.', color='orange', linewidth=2, marker='*', markersize=10, label='dash-dot')
plt.plot(x, [5, 6, 7, 8],  'm--x', alpha=0.5, label='format string')     # shorthand
plt.legend(); plt.title('Line Appearances'); plt.show()
```

---

### Q.4 (B) [3 Marks]
> Explain Axis, Ticks and Grid.
> **OR**
> Explain Networkx library with directed graph.

- **Axis:** the horizontal (x) and vertical (y) lines with scale along which data is plotted (an `Axes` object contains the `xaxis`/`yaxis`). Limits are set with `xlim()`/`ylim()`, labels with `xlabel()`/`ylabel()`.
- **Ticks:** the markers on an axis denoting positions of values; **major ticks** (labelled) and **minor ticks**. Control with `xticks()`, `yticks()`, `tick_params()`.
- **Grid:** background lines through the ticks to read values easily: `plt.grid(True, linestyle='--', color='gray')`; `axis='x'` or `'y'` limits grid to one direction; `which='minor'` for minor ticks.

```python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
plt.plot(x, y, marker='o')
plt.xticks([1, 2, 3, 4, 5], ['One', 'Two', 'Three', 'Four', 'Five'])
plt.yticks(range(0, 12, 2))
plt.xlim(0, 6); plt.ylim(0, 12)
plt.tick_params(axis='both', direction='in', length=5)
plt.grid(True, linestyle=':', alpha=0.7)
plt.show()
```
(More detail: **Paper 1 → Q.3 (B)**.)

**OR — NetworkX with a directed graph**

A **directed graph (`nx.DiGraph`)** has edges with direction: edge A→B goes **from A to B** only (e.g. web links, follower relation, task dependencies). Nodes have **in-degree** (incoming edges) and **out-degree** (outgoing edges).

```python
import networkx as nx
import matplotlib.pyplot as plt

D = nx.DiGraph()
D.add_edges_from([("A", "B"), ("A", "C"), ("B", "D"), ("C", "D"), ("D", "A")])

print("Nodes:", D.nodes())
print("Edges:", D.edges())
print("In-degree :", dict(D.in_degree()))
print("Out-degree:", dict(D.out_degree()))
print("Successors of A  :", list(D.successors("A")))     # ['B', 'C']
print("Predecessors of D:", list(D.predecessors("D")))   # ['B', 'C']
print("Shortest path A->D:", nx.shortest_path(D, "A", "D"))

nx.draw(D, with_labels=True, arrows=True, node_color="lightcoral", node_size=1200, arrowsize=20)
plt.show()
```
(NetworkX introduction: **Paper 1 → Q.2 (C)**.)

---

### Q.4 (C) [7 Marks]
> Write a python program to implement LMplot and heatmap with random data.
> **OR**
> Write a python program to implement countplot and boxplot with titanic dataset.

**`lmplot`** draws a scatter plot with a fitted **linear regression line** (and confidence band). **`heatmap`** shows a matrix as colour-coded cells.

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(0)
# Random data
df = pd.DataFrame({
    'x': np.random.rand(50) * 10,
    'group': np.random.choice(['A', 'B'], 50)
})
df['y'] = 2 * df['x'] + np.random.randn(50) * 2          # linear relation with noise
df['z'] = np.random.rand(50) * 100

# 1) lmplot (regression line)
sns.lmplot(x='x', y='y', data=df, hue='group', height=5, aspect=1.2)
plt.title('lmplot with random data')
plt.show()

# 2) heatmap of random matrix
matrix = np.random.rand(5, 5)
plt.figure(figsize=(6, 5))
sns.heatmap(matrix, annot=True, cmap='coolwarm', fmt='.2f', linewidths=0.5)
plt.title('Heatmap of random data')
plt.show()

# heatmap of correlation between columns
sns.heatmap(df[['x', 'y', 'z']].corr(), annot=True, cmap='viridis')
plt.show()
```

**OR — countplot and boxplot with Titanic:** the complete program is in **Paper 2 → Q.4 (C) OR**. Core code:
```python
import seaborn as sns, matplotlib.pyplot as plt
titanic = sns.load_dataset('titanic')
sns.countplot(x='pclass', hue='survived', data=titanic); plt.title('Survival by class'); plt.show()
sns.boxplot(x='pclass', y='age', data=titanic);          plt.title('Age by class');      plt.show()
```

---

## Q.5

### Q.5 (A) [4 Marks]
> Differentiate Supervised Learning and Unsupervised Learning.

Complete table: **Paper 1 → Q.4 (B) OR**.

| Basis | Supervised Learning | Unsupervised Learning |
|---|---|---|
| Training data | Labelled (X and y) | Unlabelled (only X) |
| Objective | Learn mapping X → y to predict | Find hidden patterns/groups |
| Feedback | Direct feedback (error vs label) | No feedback |
| Problems | Classification, Regression | Clustering, Association, Dimensionality reduction |
| Algorithms | Linear/Logistic Regression, KNN, SVM, Decision Tree | K-Means, Hierarchical, DBSCAN, PCA |
| Evaluation | Accuracy, precision, RMSE | Silhouette score, inertia (indirect) |
| Complexity | Needs labelled data (costly) | Cheaper data, but harder to interpret |
| Example | Predicting house price; spam detection | Customer segmentation |

---

### Q.5 (B) [3 Marks]
> Explain confusion matrix with an example.
> **OR**
> Explain bag of words model.

**Confusion matrix** — a table comparing actual and predicted classes of a classifier (TP, FP, FN, TN). Full explanation: **Paper 1 → Q.5 (B) OR**.

|  | Predicted Yes | Predicted No |
|---|---|---|
| **Actual Yes** | TP = 50 | FN = 10 |
| **Actual No** | FP = 5 | TN = 35 |

Accuracy = (50+35)/100 = 0.85; Precision = 50/55 = 0.91; Recall = 50/60 = 0.83; F1 = 0.87.
```python
from sklearn.metrics import confusion_matrix, classification_report
y_true = [1, 0, 1, 1, 0, 1, 0, 0]
y_pred = [1, 0, 1, 0, 0, 1, 1, 0]
print(confusion_matrix(y_true, y_pred))      # [[3 1] [1 3]]
print(classification_report(y_true, y_pred))
```

**OR — Bag of Words model:** represents text as an unordered set of words with their counts (grammar and order ignored). Full explanation and example: **Paper 2 → Q.5 (B)**.
```python
from sklearn.feature_extraction.text import CountVectorizer
docs = ["data science is fun", "python is fun"]
cv = CountVectorizer()
print(cv.fit_transform(docs).toarray())
print(cv.get_feature_names_out())   # ['data' 'fun' 'is' 'python' 'science']
# [[1 1 1 0 1]
#  [0 1 1 1 0]]
```

---

### Q.5 (C) [7 Marks]
> What is regression? Explain logistic regression with an example.
> **OR**
> What is clustering? Explain K-Mean with an example.

**Regression:** a supervised technique that predicts a **continuous numeric value** from input variables (linear regression, polynomial regression, etc.).

**Logistic Regression:** despite its name, it is a **classification** algorithm used when the output is **categorical (binary: 0/1, yes/no)**. It applies the **sigmoid function** to a linear combination of inputs to give a **probability** between 0 and 1:

**P(y=1) = 1 / (1 + e^-(b0 + b1·x))**

If P ≥ 0.5 the class is 1, else 0 (threshold adjustable). Fitted by maximum likelihood.

**Example — pass/fail from hours studied:**
```python
import numpy as np
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

hours  = np.array([[1], [2], [3], [4], [5], [6], [7], [8], [9], [10]])
passed = np.array([0, 0, 0, 0, 1, 0, 1, 1, 1, 1])

X_train, X_test, y_train, y_test = train_test_split(hours, passed, test_size=0.3, random_state=1)
model = LogisticRegression()
model.fit(X_train, y_train)

print("Accuracy:", accuracy_score(y_test, model.predict(X_test)))
print("Predict 6.5 hrs :", model.predict([[6.5]]))              # [1] -> Pass
print("Probability     :", model.predict_proba([[6.5]]))        # [[P(fail), P(pass)]]
```

**OR — Clustering & K-Means:** *Clustering* is an unsupervised technique that groups similar items together (customer segmentation, image compression). **K-Means** partitions data into K clusters: (1) choose K, (2) pick K initial centroids, (3) assign each point to the nearest centroid, (4) recompute centroids as cluster means, (5) repeat until stable. Choose K using the **Elbow method** (plot inertia vs K).

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

X = np.array([[1, 2], [1, 4], [1, 0],
              [10, 2], [10, 4], [10, 0],
              [5, 15], [6, 14], [5, 16]])

km = KMeans(n_clusters=3, random_state=0, n_init=10).fit(X)
print("Labels  :", km.labels_)
print("Centers :\n", km.cluster_centers_)
print("Predict [0, 0] ->", km.predict([[0, 0]]))
print("Inertia :", km.inertia_)

plt.scatter(X[:, 0], X[:, 1], c=km.labels_)
plt.scatter(km.cluster_centers_[:, 0], km.cluster_centers_[:, 1], c='red', marker='X', s=200)
plt.show()
```
Centres will be approximately `[1, 2]`, `[10, 2]`, `[5.33, 15]`. A complete random-data version is in **Paper 1 → Q.4 (C)**.

---

*Table of Bloom's Taxonomy / Course Outcomes printed on this paper:* Q.1–Q.2 → U (CO1/CO2); Q.3(C) → A (CO2); Q.4(A,B) → U (CO3), Q.4(C) → A (CO3); Q.5 → U (CO4).
CO1: describe data science using python tools; CO2: experiment with Beautiful Soup, NumPy and Pandas; CO3: sketch graphs using matplotlib; CO4: analyze supervised and unsupervised learning using scikit-learn.

---

# PAPER 4 — MCA Sem-3 | Winter-2024 | 18-10-2024 (2305CS303)

---

## Q.1

### Q.1 (A) [4 Marks]
> Enumerate the list and its methods with example.

A **list** is an **ordered, mutable (changeable)** collection that can hold items of different data types and allows duplicates. It is written in square brackets `[ ]` and indexed from 0.

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0], fruits[-1])      # apple cherry
print(fruits[0:2])                # ['apple', 'banana']
```
**List methods:**

| Method | Description | Example | Result |
|---|---|---|---|
| `append(x)` | Add item at end | `fruits.append("mango")` | `[..., 'mango']` |
| `insert(i, x)` | Insert at index | `fruits.insert(1, "kiwi")` | `['apple','kiwi','banana',...]` |
| `extend(iterable)` | Add many items | `fruits.extend(["fig", "lime"])` | |
| `remove(x)` | Remove first occurrence | `fruits.remove("banana")` | |
| `pop(i)` | Remove & return item at i (last if none) | `fruits.pop()` | |
| `clear()` | Remove all items | `fruits.clear()` | `[]` |
| `index(x)` | Index of first occurrence | `[1,2,3].index(2)` | `1` |
| `count(x)` | Number of occurrences | `[1,2,2].count(2)` | `2` |
| `sort()` | Sort in place | `nums.sort(reverse=True)` | |
| `reverse()` | Reverse in place | `nums.reverse()` | |
| `copy()` | Shallow copy | `b = nums.copy()` | |

```python
nums = [5, 2, 8, 1]
nums.append(9);  print(nums)        # [5, 2, 8, 1, 9]
nums.insert(0, 7); print(nums)      # [7, 5, 2, 8, 1, 9]
nums.remove(8);  print(nums)        # [7, 5, 2, 1, 9]
print(nums.pop())                   # 9
nums.sort();     print(nums)        # [1, 2, 5, 7]
nums.reverse();  print(nums)        # [7, 5, 2, 1]
print(len(nums), max(nums), min(nums), sum(nums))   # 4 7 1 15
```

---

### Q.1 (B) [3 Marks]
> Differentiate between the tuple and sets in python.
> **OR**
> Differentiate between the List and sets in python.

**Tuple vs Set**

| Basis | Tuple | Set |
|---|---|---|
| Syntax | `( )` → `t = (1, 2, 3)` | `{ }` → `s = {1, 2, 3}` |
| Order | **Ordered** | **Unordered** |
| Indexing / slicing | Supported (`t[0]`) | Not supported |
| Mutability | **Immutable** | **Mutable** (add/remove), but elements must be immutable |
| Duplicates | Allowed | **Not allowed** (auto removed) |
| Methods | `count()`, `index()` | `add()`, `remove()`, `union()`, `intersection()`, `difference()` |
| Use | Fixed data, dictionary keys | Unique items, membership test, set operations |

```python
t = (1, 2, 2, 3);  print(t[1], t.count(2))   # 2 2
s = {1, 2, 2, 3};  print(s)                  # {1, 2, 3}
s.add(4)           # allowed ; t.append(4) -> AttributeError
```

**OR — List vs Set**

| Basis | List | Set |
|---|---|---|
| Syntax | `[ ]` | `{ }` or `set()` |
| Order | Ordered | Unordered |
| Duplicates | Allowed | Not allowed |
| Indexing | Yes | No |
| Mutability | Mutable | Mutable |
| Speed of membership test | O(n) | O(1) average |
| Methods | `append`, `insert`, `sort`, `pop` | `add`, `union`, `intersection`, `discard` |

```python
l = [1, 2, 2, 3]   # [1, 2, 2, 3]
s = set(l)         # {1, 2, 3}  -> list(set(l)) removes duplicates
```

---

### Q.1 (C) [7 Marks]
> What is data type? List out the types of data types with example.
> **OR**
> Explain variable with suitable example.

A **data type** defines the **kind of value** a variable can hold and the operations that can be performed on it. Python is **dynamically typed** (type decided at run time) — use `type()` to check it.

| Category | Data type | Example | Description |
|---|---|---|---|
| **Numeric** | `int` | `x = 25` | Whole numbers of any size |
| | `float` | `pi = 3.14` | Decimal numbers |
| | `complex` | `z = 2 + 3j` | Real + imaginary |
| **Text** | `str` | `s = "Python"` | Sequence of characters |
| **Boolean** | `bool` | `flag = True` | True / False |
| **Sequence** | `list` | `[1, "a", 2.5]` | Ordered, mutable |
| | `tuple` | `(1, 2, 3)` | Ordered, immutable |
| | `range` | `range(5)` | Sequence of numbers |
| **Mapping** | `dict` | `{"id": 1, "name": "A"}` | Key-value pairs |
| **Set** | `set` | `{1, 2, 3}` | Unordered, unique items |
| | `frozenset` | `frozenset([1, 2])` | Immutable set |
| **Binary** | `bytes`, `bytearray` | `b"abc"` | Byte sequences |
| **None** | `NoneType` | `x = None` | Absence of value |

```python
a = 10;          print(type(a))    # <class 'int'>
b = 3.14;        print(type(b))    # <class 'float'>
c = 2 + 3j;      print(type(c))    # <class 'complex'>
d = "Hello";     print(type(d))    # <class 'str'>
e = True;        print(type(e))    # <class 'bool'>
f = [1, 2, 3];   print(type(f))    # <class 'list'>
g = (1, 2, 3);   print(type(g))    # <class 'tuple'>
h = {"a": 1};    print(type(h))    # <class 'dict'>
i = {1, 2, 3};   print(type(i))    # <class 'set'>
j = None;        print(type(j))    # <class 'NoneType'>
print(int("5") + 2, float(3), str(10), list("abc"))   # type casting
```
**Mutable:** list, dict, set. **Immutable:** int, float, str, tuple, bool, frozenset.

**OR — Variable**

A **variable** is a **named memory location** used to store data. In Python no declaration is needed — a variable is created when a value is assigned with `=`, and its type is decided by the value.

**Rules for naming:** start with a letter or underscore (not a digit); only letters, digits, underscore; case-sensitive (`age` ≠ `Age`); no keywords (`for`, `if`, `class`).

```python
name = "Amit"           # str
age = 21                # int
height = 5.9            # float
is_student = True       # bool
print(name, age, height, is_student)

x = y = z = 0           # same value to many variables
a, b, c = 1, 2.5, "hi"  # multiple assignment
a, b = b, a             # swap
age = "twenty-one"      # dynamic typing: type changes on reassignment
print(type(age))        # <class 'str'>

# Scope
g = 100                 # global variable
def show():
    l = 5               # local variable
    print(g, l)
show()
```

---

## Q.2

### Q.2 (A) [4 Marks]
> Write a program to print the fibonacci series upto n_terms using Recursion.

Fibonacci: 0, 1, 1, 2, 3, 5, 8, … where each term = sum of the previous two. Recursive definition: **fib(0)=0, fib(1)=1, fib(n)=fib(n-1)+fib(n-2)**.

```python
def fibonacci(n):
    if n <= 1:                              # base case
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)   # recursive case

n_terms = int(input("Enter number of terms: "))

if n_terms <= 0:
    print("Please enter a positive integer")
else:
    print("Fibonacci series:")
    for i in range(n_terms):
        print(fibonacci(i), end=" ")
```
**Output (n_terms = 8):** `0 1 1 2 3 5 8 13`

---

### Q.2 (B) [3 Marks]
> Explain For loop statement with any example.
> **OR**
> Explain While loop statement with any example.

**`for` loop** iterates over the items of any iterable (list, tuple, string, dict, set, `range()`), executing the block once per item. It is used when the number of iterations is known.

**Syntax:**
```python
for variable in iterable:
    statements
else:          # optional - runs if loop finishes without break
    statements
```
```python
for i in range(1, 6):             # 1 to 5
    print(i, end=" ")             # 1 2 3 4 5

for fruit in ["apple", "banana"]:
    print(fruit)

for ch in "Hi":
    print(ch)                     # H  i

total = 0
for n in range(1, 11):
    total += n
print("Sum =", total)             # Sum = 55
```
`range(start, stop, step)` generates the sequence; `break` exits the loop, `continue` skips an iteration.

**OR — `while` loop** repeats a block **as long as a condition is True**; used when the number of iterations is not known in advance. The loop variable must be updated, otherwise an infinite loop occurs.

**Syntax:**
```python
while condition:
    statements
else:
    statements   # runs when condition becomes False (not on break)
```
```python
i = 1
while i <= 5:
    print(i, end=" ")      # 1 2 3 4 5
    i += 1

# Factorial of a number
n = 5; fact = 1
while n > 0:
    fact *= n
    n -= 1
print("Factorial =", fact)   # 120
```

---

### Q.2 (C) [7 Marks]
> Explain Types of Python Function Arguments with any example.
> **OR**
> Write a program to use of nested if statement.

A **function** is a reusable block of code defined with `def`. **Parameters** are names in the definition; **arguments** are the values passed when calling. Python supports **four types** of arguments:

**1. Positional (required) arguments** — matched by position/order; the number must match.
```python
def student(name, age):
    print(name, age)
student("Amit", 21)         # Amit 21
student(21, "Amit")         # wrong order -> 21 Amit
```
**2. Keyword arguments** — passed as `name=value`; order does not matter.
```python
student(age=21, name="Amit")   # Amit 21
```
**3. Default arguments** — parameter has a default value used when the argument is omitted (default parameters must come after non-default ones).
```python
def greet(name, msg="Good Morning"):
    print(msg, name)
greet("Riya")                  # Good Morning Riya
greet("Riya", "Hello")         # Hello Riya
```
**4. Variable-length arguments**
- `*args` — any number of positional arguments, collected in a **tuple**.
- `**kwargs` — any number of keyword arguments, collected in a **dictionary**.
```python
def add(*args):
    return sum(args)
print(add(1, 2, 3, 4))         # 10

def info(**kwargs):
    for k, v in kwargs.items():
        print(k, "=", v)
info(name="Amit", city="Rajkot")   # name = Amit / city = Rajkot

def demo(a, b=2, *args, **kwargs):  # all together
    print(a, b, args, kwargs)
demo(1, 3, 4, 5, x=10)             # 1 3 (4, 5) {'x': 10}
```
Rules for order: positional → default → `*args` → `**kwargs`.

**OR — Nested if statement** — an `if` placed inside another `if` (or `elif`/`else`); the inner condition is evaluated only when the outer condition is True.

```python
# Program: find the largest of three numbers and check eligibility to vote
a = int(input("Enter first number : "))
b = int(input("Enter second number: "))
c = int(input("Enter third number : "))

if a >= b:
    if a >= c:
        print("Largest is", a)
    else:
        print("Largest is", c)
else:
    if b >= c:
        print("Largest is", b)
    else:
        print("Largest is", c)

# Second example - voting
age = int(input("Enter age: "))
citizen = input("Are you a citizen (yes/no)? ")
if age >= 18:
    if citizen.lower() == "yes":
        print("Eligible to vote")
    else:
        print("Not a citizen")
else:
    print("Under age")
```
**Sample:** inputs 10, 25, 15 → `Largest is 25`.

---

## Q.3

### Q.3 (A) [4 Marks]
> Explain Type of Indexing in NumPy.

NumPy supports several ways to access array elements:

**1. Basic indexing (integer indexing)** — access by position; negative index counts from the end; multi-dimensional `arr[row, col]`.
```python
import numpy as np
a = np.array([10, 20, 30, 40, 50])
print(a[0], a[-1])               # 10 50
m = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(m[1, 2])                   # 6   (row 1, col 2)
```
**2. Slicing** — `arr[start:stop:step]`; returns a **view** (not a copy).
```python
print(a[1:4])                    # [20 30 40]
print(a[::2])                    # [10 30 50]
print(m[0:2, 1:3])               # [[2 3] [5 6]]
print(m[:, 0])                   # first column [1 4 7]
```
**3. Fancy (integer-array) indexing** — pass a list/array of indices; returns a **copy**.
```python
print(a[[0, 2, 4]])              # [10 30 50]
print(m[[0, 2], [1, 2]])         # [2 9] -> elements (0,1) and (2,2)
```
**4. Boolean (mask) indexing** — select elements using a condition.
```python
print(a[a > 25])                 # [30 40 50]
```
**5. Ellipsis / newaxis** — `arr[..., 0]` selects across all leading dimensions; `a[:, np.newaxis]` adds a dimension.

---

### Q.3 (B) [3 Marks]
> Write an out of the following code.
> ```python
> import numpy as np
> a = np.array([5, 72, 13, 100])
> b = np.array([2, 5, 10, 30])
>
> add_ans = a+b
> print(add_ans)
>
> add_ans = np.add(a, b)
> print(add_ans)
>
> c = np.array([1, 2, 3, 4])
> add_ans = a+b+c
> print(add_ans)
>
> add_ans = np.add(a, b, c)
> print(add_ans)
> ```
> **OR**
> Explain any two NumPy Arithmetic Operators.

**Output:**
```
[  7  77  23 130]
[  7  77  23 130]
[  8  79  26 134]
[  7  77  23 130]
```
**Step-by-step explanation:**
1. `a + b` is element-wise: 5+2=7, 72+5=77, 13+10=23, 100+30=130 → `[7 77 23 130]`.
2. `np.add(a, b)` is the same operation → `[7 77 23 130]`.
3. `a + b + c` = `[7 77 23 130] + [1 2 3 4]` = `[8 79 26 134]`.
4. `np.add(a, b, c)` — the **third positional argument of a ufunc is the `out` parameter**. So the result of a+b is stored **into `c`** (c is overwritten) and also returned → `[7 77 23 130]` (it is *not* a three-array addition).

**OR — Two NumPy arithmetic operators**

| Operator | Function | Description | Example (`a=[10,20,30]`, `b=[1,2,3]`) |
|---|---|---|---|
| `+` | `np.add(a, b)` | Element-wise addition | `[11 22 33]` |
| `-` | `np.subtract(a, b)` | Element-wise subtraction | `[ 9 18 27]` |
| `*` | `np.multiply(a, b)` | Element-wise multiplication (not matrix product) | `[10 40 90]` |
| `/` | `np.divide(a, b)` | Element-wise true division | `[10. 10. 10.]` |
| `//` | `np.floor_divide` | Floor division | |
| `%` | `np.mod(a, b)` | Remainder | |
| `**` | `np.power(a, b)` | Exponent | `[10 400 27000]` |

```python
import numpy as np
a = np.array([10, 20, 30]); b = np.array([1, 2, 3])
print(a + b)    # [11 22 33]       (addition)
print(a * b)    # [10 40 90]       (multiplication)
print(a * 2)    # [20 40 60]       (broadcasting with a scalar)
```
Operations work **element-wise** and use **broadcasting** when shapes differ (e.g. scalar with array).

---

### Q.3 (C) [7 Marks]
> List any 5 Array creation function with description.
> **OR**
> List out any 5 NumPy data types with description.

| # | Function | Description | Example → Output |
|---|---|---|---|
| 1 | `np.array()` | Creates an array from a list/tuple | `np.array([1, 2, 3])` → `[1 2 3]` |
| 2 | `np.zeros(shape)` | Array of all zeros (float default) | `np.zeros((2, 3))` → `[[0. 0. 0.] [0. 0. 0.]]` |
| 3 | `np.ones(shape)` | Array of all ones | `np.ones(3)` → `[1. 1. 1.]` |
| 4 | `np.arange(start, stop, step)` | Evenly spaced values by step (stop excluded) | `np.arange(0, 10, 3)` → `[0 3 6 9]` |
| 5 | `np.linspace(start, stop, num)` | `num` evenly spaced values, stop included | `np.linspace(0, 1, 5)` → `[0. 0.25 0.5 0.75 1.]` |
| + | `np.eye(n)` | Identity matrix | `np.eye(2)` |
| + | `np.full(shape, v)` | Array filled with value v | `np.full((2,2), 5)` |
| + | `np.random.rand(...)` | Random floats in [0,1) | `np.random.rand(3)` |

```python
import numpy as np
print(np.array([[1, 2], [3, 4]]))
print(np.zeros((2, 2)))
print(np.ones((2, 3), dtype=int))
print(np.arange(5))
print(np.linspace(0, 10, 3))      # [ 0.  5. 10.]
```

**OR — Five NumPy data types**

| dtype | Code | Description | Example |
|---|---|---|---|
| `int32` / `int64` | `'i4'`, `'i8'` | Signed integer (32/64-bit) | `np.array([1,2,3], dtype=np.int32)` |
| `float32` / `float64` | `'f4'`, `'f8'` | Floating-point numbers | `np.array([1.5, 2.5], dtype=np.float64)` |
| `bool_` | `'?'` | True/False values | `np.array([True, False])` |
| `complex128` | `'c16'` | Complex numbers | `np.array([1+2j])` |
| `str_` (unicode) | `'U'` | Fixed-length strings | `np.array(['a','bb'], dtype='U2')` |
| `uint8` | `'u1'` | Unsigned 8-bit integer (0–255), used for images | `np.array([0,255], dtype=np.uint8)` |
| `datetime64` | `'M8'` | Dates/times | `np.array(['2024-01-01'], dtype='datetime64')` |

```python
a = np.array([1, 2, 3], dtype=np.float32)
print(a.dtype)                 # float32
b = a.astype(np.int64)         # type conversion
print(b.dtype)                 # int64
```

---

## Q.4

### Q.4 (A) [4 Marks]
> Create a DataFrame by passing a dictionary of Series objects:
> ```python
> import pandas as pd
> people_dict = {
>   "weight": pd.Series([68, 83, 112], index=["alice", "bob", "charles"]),
>   "birthyear": pd.Series([1984, 1985, 1992], index=["bob", "alice", "charles"], name="year"),
>   "children": pd.Series([0, 3], index=["charles", "bob"]),
>   "hobby": pd.Series(["Biking", "Dancing"], index=["alice", "bob"]),
> }
> people = pd.DataFrame(people_dict)
> people
> ```

When a DataFrame is built from a dictionary of Series, **dictionary keys become column names** and Series are **aligned on their index labels**; the row index is the **union (sorted)** of all indexes, and **missing labels are filled with NaN**. The Series `name="year"` is ignored (the dict key `"birthyear"` is used as the column name).

**Output:**
```
         weight  birthyear  children    hobby
alice        68       1985       NaN   Biking
bob          83       1984       3.0  Dancing
charles     112       1992       0.0      NaN
```
**Explanation:**
- `birthyear` — Series given as bob=1984, alice=1985, charles=1992 is re-aligned: alice=1985, bob=1984, charles=1992.
- `children` has only charles(0) and bob(3) → alice gets **NaN**; the column becomes `float64` (3.0, 0.0) because NaN is a float.
- `hobby` has only alice and bob → charles gets **NaN**.

Useful follow-ups: `people.dtypes`, `people.isnull()`, `people.fillna(0)`, `people["weight"]`, `people.loc["bob"]`.

---

### Q.4 (B) [3 Marks]
> What is Reset_Index() in Pandas?
> **OR**
> Explain use of Reset_Index() method in pandas.

`reset_index()` **resets the index of a DataFrame/Series to the default integer index (0, 1, 2 …)**. The old index is moved into a **new column** (unless `drop=True`). It is commonly used after filtering/sorting/groupby, or to convert a MultiIndex back into columns.

**Syntax:** `df.reset_index(level=None, drop=False, inplace=False)`
- `drop=True` — discard the old index instead of adding it as a column.
- `inplace=True` — modify the same DataFrame.
- `level` — reset only particular level(s) of a MultiIndex.

```python
import pandas as pd
df = pd.DataFrame({'Name': ['A', 'B', 'C', 'D'], 'Marks': [90, 55, 80, 45]})
f = df[df['Marks'] > 50]            # index becomes 0,1,2 -> after filter: 0,1,2 (D removed)
f2 = df[df['Marks'] < 85]           # index: 1, 2, 3
print(f2.reset_index())             # old index kept as column 'index'
#    index Name  Marks
# 0      1    B     55
# 1      2    C     80
# 2      3    D     45
print(f2.reset_index(drop=True))    # clean 0,1,2 index, no extra column

s = df.groupby('Name')['Marks'].sum().reset_index()   # groupby result back to a DataFrame
```
**Uses:** (1) restore a continuous index after filtering, (2) turn index into a column, (3) flatten MultiIndex, (4) after `sort_values()`.

---

### Q.4 (C) [7 Marks]
> List out any 5 pandas series function with description.
> **OR**
> Explain Concatenation and Merge with example.

A pandas **Series** is a one-dimensional labelled array. Five commonly used functions:

| # | Function | Description | Example |
|---|---|---|---|
| 1 | `head(n)` / `tail(n)` | First / last n elements | `s.head(2)` |
| 2 | `sum()` / `mean()` / `max()` / `min()` | Aggregate statistics | `s.mean()` → `30.0` |
| 3 | `value_counts()` | Frequency of each unique value | `pd.Series(['a','b','a']).value_counts()` → a:2, b:1 |
| 4 | `sort_values()` | Sort by values (`ascending=False` for reverse) | `s.sort_values(ascending=False)` |
| 5 | `apply(func)` / `map()` | Apply a function to every element | `s.apply(lambda x: x*2)` |
| + | `unique()`, `nunique()` | Distinct values / count | |
| + | `isnull()`, `fillna()`, `dropna()` | Missing-value handling | |
| + | `describe()` | Count, mean, std, quartiles | |

```python
import pandas as pd
s = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])
print(s.head(2))                       # a 10, b 20
print(s.sum(), s.mean(), s.max())      # 150 30.0 50
print(s.sort_values(ascending=False))  # e 50, d 40 ...
print(s.apply(lambda x: x * 2))        # a 20, b 40 ...
print(pd.Series(['x', 'y', 'x', 'x']).value_counts())   # x 3, y 1
print(s.describe())
```

**OR — Concatenation and Merge**

**Concatenation (`pd.concat`)** — **stacks** DataFrames/Series along an axis: `axis=0` (default) appends **rows** one below another; `axis=1` places them **side by side** (aligns on index). No key matching needed.

**Merge (`pd.merge`)** — **joins** DataFrames on **common column(s)** (like SQL JOIN): `how='inner' | 'left' | 'right' | 'outer'`.

```python
import pandas as pd
df1 = pd.DataFrame({'id': [1, 2], 'name': ['Amit', 'Riya']})
df2 = pd.DataFrame({'id': [3, 4], 'name': ['John', 'Sara']})
marks = pd.DataFrame({'id': [1, 2, 5], 'marks': [80, 90, 70]})

# Concatenation - rows
print(pd.concat([df1, df2], ignore_index=True))
#    id  name
# 0   1  Amit
# 1   2  Riya
# 2   3  John
# 3   4  Sara

# Concatenation - columns
print(pd.concat([df1, marks], axis=1))

# Merge - on common key 'id'
print(pd.merge(df1, marks, on='id'))                  # inner
#    id  name  marks
# 0   1  Amit     80
# 1   2  Riya     90
print(pd.merge(df1, marks, on='id', how='outer'))     # all ids 1,2,5 (NaN where missing)
```
| Concat | Merge |
|---|---|
| Joins by position/index along an axis | Joins by matching key column values |
| No key required | Needs common key(s) |
| Combines similar-structure data | Combines related tables |

---

## Q.5

### Q.5 (A) [4 Marks]
> Draw a graph for following code
> ```python
> import matplotlib.pyplot as plt
> import numpy as np
> # Define X and Y variable data
> x = np.array([1, 2, 3, 4])
> y = x*2
> plt.plot(x, y)
> plt.xlabel("X-axis")  # add X-axis label
> plt.ylabel("Y-axis")  # add Y-axis label
> plt.title("Any suitable title")  # add title
> plt.show()
> ```

Here `y = x*2 = [2, 4, 6, 8]`, so the points are **(1,2), (2,4), (3,6), (4,8)** — they lie on a **straight line with a positive slope of 2** passing through the origin direction.

```
 Any suitable title
Y-axis
  8 |                      *
  7 |                  /
  6 |              *
  5 |          /
  4 |      *
  3 |   /
  2 | *
    +-----+-----+-----+-----+--
      1     2     3     4     X-axis
```
- Line colour: default blue (solid line `-`), no markers.
- X-axis range ≈ 1–4, Y-axis range ≈ 2–8; x-label "X-axis", y-label "Y-axis", title "Any suitable title".

---

### Q.5 (B) [3 Marks]
> Draw a graph for following code
> ```python
> import matplotlib.pyplot as plt
> x = [10,20,30,40,50]
> y = [30,30,30,30,30]
> plt.plot(x, y)
> plt.show()
> ```
> **OR**
> Draw a graph for following code (two lines with legend)
> ```python
> x = [10,20,30,40,50]
> y = [30,30,30,30,30]
> plt.plot(x, y, label = "line 1")
> plt.plot(y, x, label = "line 2")
> plt.legend()
> plt.show()
> ```

**Graph for the first code:** all y-values are 30, so the plot is a **horizontal straight line at y = 30** from x = 10 to x = 50 (points (10,30) … (50,30)).
```
 y
 31 |
 30 |*------*------*------*------*
 29 |
    +------+------+------+------+--
      10     20     30     40     50   x
```
No labels/title/legend are present.

**OR — two lines:**
- `plt.plot(x, y, label="line 1")` → horizontal line at **y = 30**, x from 10 to 50 (blue).
- `plt.plot(y, x, label="line 2")` → here x-values are `[30,30,30,30,30]` and y-values are `[10,20,30,40,50]` → a **vertical line at x = 30**, y from 10 to 50 (orange).
- The two lines **intersect at the point (30, 30)**, forming a plus (+) shape.
- `plt.legend()` shows a box (usually upper-right/best location) with **"line 1" (blue)** and **"line 2" (orange)**.
```
 y
 50 |        |
 40 |        |
 30 |--------+---------    line 1: horizontal (y=30)
 20 |        |             line 2: vertical (x=30)
 10 |        |
    +--------+--------- x
   10   20  30  40  50
```

---

### Q.5 (C) [7 Marks]
> Write a code and draw a line in a diagram from position (1, 3) to (2, 8) then to (6, 1) and finally to position (8, 10):
> **OR**
> Explain type of Types of Charts in Matplotlib

The x-coordinates are `[1, 2, 6, 8]` and the y-coordinates are `[3, 8, 1, 10]`; `plt.plot()` joins the points in the given order.

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 2, 6, 8])
ypoints = np.array([3, 8, 1, 10])

plt.plot(xpoints, ypoints, marker='o', color='blue', linewidth=2)
plt.title("Line through (1,3) -> (2,8) -> (6,1) -> (8,10)")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.grid(True)
plt.show()
```
**Resulting diagram:** the line rises steeply from (1,3) to (2,8), falls sharply to (6,1), then rises steeply to the final point (8,10) — a zig-zag "N / W" shaped line.

**OR — Types of charts in Matplotlib**

| Chart | Function | Use | Example |
|---|---|---|---|
| **Line plot** | `plt.plot()` | Trend over time / continuous data | `plt.plot(x, y)` |
| **Bar chart** | `plt.bar()` / `plt.barh()` | Compare categories | `plt.bar(['A','B'], [10, 20])` |
| **Histogram** | `plt.hist()` | Distribution of a numeric variable (bins) | `plt.hist(data, bins=5)` |
| **Scatter plot** | `plt.scatter()` | Relationship between two variables | `plt.scatter(x, y)` |
| **Pie chart** | `plt.pie()` | Proportion/percentage of a whole | `plt.pie([30, 70], labels=['A','B'], autopct='%1.1f%%')` |
| **Box plot** | `plt.boxplot()` | Median, quartiles, outliers | `plt.boxplot(data)` |
| **Area plot** | `plt.fill_between()` / `stackplot()` | Cumulative magnitude over time | |
| **Stem plot** | `plt.stem()` | Discrete data | |
| **Violin plot** | `plt.violinplot()` | Distribution shape | |
| **Heatmap/Image** | `plt.imshow()` | Matrix as colours | |
| **Subplots** | `plt.subplots()` | Several charts in one figure | |

```python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(2, 2, figsize=(8, 6))
ax[0, 0].plot([1, 2, 3], [2, 4, 6]);             ax[0, 0].set_title('Line')
ax[0, 1].bar(['A', 'B', 'C'], [5, 9, 3]);        ax[0, 1].set_title('Bar')
ax[1, 0].scatter([1, 2, 3, 4], [4, 1, 3, 2]);    ax[1, 0].set_title('Scatter')
ax[1, 1].pie([40, 60], labels=['X', 'Y'], autopct='%1.0f%%'); ax[1, 1].set_title('Pie')
plt.tight_layout(); plt.show()
```

---

# PAPER 5 — MCA Sem-3 | Winter-2025 | 11-10-2025 (2305CS303)

---

## Q.1

### Q.1 (A) [4 Marks]
> List any four advantages of Python over other programming languages.

1. **Simple and readable syntax** — close to English, no semicolons/braces; fewer lines than Java/C++ (e.g. printing is just `print("Hello")`). Easy to learn and maintain.
2. **Extensive standard library and third-party packages** — NumPy, Pandas, Matplotlib, scikit-learn, Django, Flask, TensorFlow; "batteries included" saves development time.
3. **Interpreted and dynamically typed** — code runs line by line without a compile step; no need to declare variable types, so development and debugging are faster.
4. **Cross-platform & open source** — the same program runs on Windows, Linux, macOS; free with a large community.
5. **Multi-paradigm support** — procedural, object-oriented and functional programming.
6. **Wide application areas** — data science, AI/ML, web development, automation, scripting, game development; integrates easily with C/C++/Java, databases and APIs.
7. **High productivity** — rapid prototyping; strong support from Jupyter Notebook etc.

*(Any four are sufficient: write 1–4 with a one-line example each.)*

---

### Q.1 (B) [3 Marks]
> What is the difference between identity operators and membership operators in Python? Explain with small examples.
> **OR**
> What are magic commands in Python? Give any two examples commonly used in Jupyter Notebook.

| Basis | Identity operators | Membership operators |
|---|---|---|
| Operators | `is`, `is not` | `in`, `not in` |
| Purpose | Check whether two variables refer to the **same object in memory** (same `id()`) | Check whether a value is **present in a sequence/collection** (list, tuple, string, set, dict keys) |
| Compares | Object identity (memory location) | Presence/absence of an element |
| Returns | `True`/`False` | `True`/`False` |

```python
# Identity operators
a = [1, 2, 3]
b = a            # same object
c = [1, 2, 3]    # equal value, different object
print(a is b)        # True
print(a is c)        # False  (different objects)
print(a == c)        # True   (== compares values)
print(a is not c)    # True

# Membership operators
fruits = ["apple", "banana", "cherry"]
print("banana" in fruits)        # True
print("mango" not in fruits)     # True
print("a" in "Python")           # False
print(2 in {1: "x", 2: "y"})     # True (checks keys)
```

**OR — Magic commands:** special IPython/Jupyter commands starting with `%` (line magic — acts on one line) or `%%` (cell magic — acts on the whole cell) that provide shortcuts for tasks like timing, running files and plotting. They are not part of core Python.

Two commonly used examples:
1. **`%timeit`** — measures execution time by running the statement many times.
```python
%timeit sum(range(1000))      # 15 µs ± 200 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
```
2. **`%matplotlib inline`** — displays Matplotlib plots inside the notebook.
```python
%matplotlib inline
import matplotlib.pyplot as plt
plt.plot([1, 2, 3]); plt.show()
```
Others: `%run file.py`, `%time`, `%who`, `%pwd`, `%lsmagic`, `%reset`, `%%writefile`. Details: **Paper 2 → Q.1 (C)**.

---

### Q.1 (C) [7 Marks]
> What is Datatype? List out different Datatypes in Python with example.
> **OR**
> Explain with examples how the break, continue, and pass keywords affect the flow of loops in Python.

A **data type** specifies the type of value a variable holds and what operations are allowed on it. Python is dynamically typed; `type()` shows the type. The complete categorised list with examples is in **Paper 4 → Q.1 (C)**. Summary:

| Category | Types | Example |
|---|---|---|
| Numeric | `int`, `float`, `complex` | `10`, `3.14`, `2+3j` |
| Text | `str` | `"Python"` |
| Boolean | `bool` | `True`, `False` |
| Sequence | `list`, `tuple`, `range` | `[1,2]`, `(1,2)`, `range(5)` |
| Mapping | `dict` | `{"a": 1}` |
| Set | `set`, `frozenset` | `{1, 2, 3}` |
| Binary | `bytes`, `bytearray`, `memoryview` | `b"hi"` |
| None | `NoneType` | `None` |

```python
x = 10;          print(type(x))   # <class 'int'>
y = 3.14;        print(type(y))   # <class 'float'>
z = 2 + 3j;      print(type(z))   # <class 'complex'>
s = "Hello";     print(type(s))   # <class 'str'>
b = True;        print(type(b))   # <class 'bool'>
l = [1, 2, 3];   print(type(l))   # <class 'list'>
t = (1, 2, 3);   print(type(t))   # <class 'tuple'>
d = {"id": 1};   print(type(d))   # <class 'dict'>
st = {1, 2, 3};  print(type(st))  # <class 'set'>
n = None;        print(type(n))   # <class 'NoneType'>
```
*Mutable:* list, dict, set. *Immutable:* int, float, str, tuple, bool, frozenset.

**OR — `break`, `continue`, `pass`**

| Keyword | Effect on loop |
|---|---|
| `break` | **Terminates** the loop immediately; control moves to the statement after the loop |
| `continue` | **Skips** the rest of the current iteration and jumps to the next iteration |
| `pass` | **Does nothing** (null statement); a placeholder where a statement is syntactically required; loop flow is unchanged |

```python
# break
for i in range(1, 10):
    if i == 5:
        break
    print(i, end=" ")        # 1 2 3 4

# continue
for i in range(1, 6):
    if i == 3:
        continue
    print(i, end=" ")        # 1 2 4 5      (3 skipped)

# pass
for i in range(1, 4):
    if i == 2:
        pass                 # placeholder, nothing happens
    print(i, end=" ")        # 1 2 3

def todo(): pass             # empty function / class body
```
`else` block of a loop runs only if the loop ends **without** `break`.

---

## Q.2

### Q.2 (A) [4 Marks]
> List any four commonly used string methods in Python and explain their purpose.

| Method | Purpose | Example | Output |
|---|---|---|---|
| `upper()` / `lower()` | Convert to upper / lower case | `"python".upper()` | `'PYTHON'` |
| `strip()` | Remove leading/trailing whitespace (`lstrip`, `rstrip`) | `"  hi  ".strip()` | `'hi'` |
| `replace(old, new)` | Replace all occurrences of a substring | `"I like Java".replace("Java","Python")` | `'I like Python'` |
| `split(sep)` | Split string into a list | `"a,b,c".split(",")` | `['a','b','c']` |
| `join(list)` | Join list items into a string | `"-".join(['a','b'])` | `'a-b'` |
| `find(sub)` | Index of first occurrence (-1 if not found) | `"hello".find("l")` | `2` |
| `startswith()` / `endswith()` | Test prefix / suffix | `"data.csv".endswith(".csv")` | `True` |
| `capitalize()` / `title()` | First letter capital / title case | `"hello world".title()` | `'Hello World'` |
| `count(sub)` | Number of occurrences | `"banana".count("a")` | `3` |

```python
s = "  Data Science  "
print(s.strip().upper())      # DATA SCIENCE
print(s.replace("Data", "Big"))
print("a,b,c".split(","))     # ['a', 'b', 'c']
print("-".join(["x", "y"]))   # x-y
```
Strings are **immutable** — these methods return a **new** string.

---

### Q.2 (B) [3 Marks]
> What is a docstring in Python? How is it useful? Provide a small example.
> **OR**
> Explain lambda function in Python. Write a simple lambda function to double a number.

A **docstring** (documentation string) is a **string literal written as the first statement** of a module, function, class or method, enclosed in triple quotes `""" """`. It documents what the code does and is stored in the object's `__doc__` attribute.

**Usefulness:** documents code, readable by `help()` and `__doc__`, used by IDE tooltips and auto-documentation tools (Sphinx), improves maintainability and team understanding.

```python
def add(a, b):
    """Return the sum of two numbers.

    Parameters: a (int), b (int)
    Returns: int - sum of a and b
    """
    return a + b

print(add.__doc__)     # prints the docstring
help(add)              # displays formatted documentation
```
(Comments `#` are ignored by Python; docstrings are accessible at run time.)

**OR — Lambda function:** a small **anonymous (nameless) function** defined with the keyword `lambda`, with **any number of arguments but only one expression** whose value is returned automatically.

**Syntax:** `lambda arguments: expression`

```python
double = lambda x: x * 2          # lambda to double a number
print(double(5))                  # 10

add = lambda a, b: a + b
print(add(3, 4))                  # 7

# Common use with map / filter / sorted
nums = [1, 2, 3, 4]
print(list(map(lambda x: x * 2, nums)))          # [2, 4, 6, 8]
print(list(filter(lambda x: x % 2 == 0, nums)))  # [2, 4]
print(sorted([(1, 'b'), (2, 'a')], key=lambda t: t[1]))   # [(2,'a'), (1,'b')]
```
**Equivalent normal function:** `def double(x): return x * 2`.

---

### Q.2 (C) [7 Marks]
> Compare List, Tuple, Set, and Dictionary in Python.
> **OR**
> Explain the different types of function arguments in Python with examples.

| Feature | List | Tuple | Set | Dictionary |
|---|---|---|---|---|
| Syntax | `[1, 2, 3]` | `(1, 2, 3)` | `{1, 2, 3}` | `{"a": 1, "b": 2}` |
| Ordered | Yes | Yes | No | Yes (insertion order, Python 3.7+) |
| Mutable | Yes | **No** (immutable) | Yes (add/remove) | Yes |
| Duplicates | Allowed | Allowed | **Not allowed** | Keys unique; values may repeat |
| Indexing | By position `l[0]` | By position `t[0]` | Not supported | By **key** `d["a"]` |
| Elements | Any | Any | Immutable/hashable only | Key: hashable; value: any |
| Speed | Normal | Faster than list (fixed) | Fast membership (O(1)) | Fast lookup by key (O(1)) |
| Memory | More | Less | More | More |
| Creation | `list()` | `tuple()` | `set()` | `dict()` |
| Common methods | `append`, `pop`, `sort`, `insert` | `count`, `index` | `add`, `remove`, `union`, `intersection` | `keys`, `values`, `items`, `get`, `update` |
| Use case | Ordered collection that changes | Fixed data, dict keys | Unique items, set maths | Key-value mapping (records, JSON) |

```python
l = [1, 2, 2, 3];   l.append(4)             # [1, 2, 2, 3, 4]
t = (1, 2, 2, 3);   print(t[1])             # 2   (t[1]=5 -> TypeError)
s = {1, 2, 2, 3};   print(s)                # {1, 2, 3}
d = {"name": "Amit", "age": 21}
print(d["name"], d.get("city", "NA"))       # Amit NA
d["city"] = "Rajkot"
```

**OR — Types of function arguments:** Python supports **positional, keyword, default and variable-length (`*args`, `**kwargs`)** arguments. The complete explanation with examples is in **Paper 4 → Q.2 (C)**. Quick summary:

```python
def demo(a, b=10, *args, **kwargs):
    print(a, b, args, kwargs)

demo(1)                        # positional + default     -> 1 10 () {}
demo(b=5, a=2)                 # keyword arguments        -> 2 5 () {}
demo(1, 2, 3, 4, x=7, y=8)     # *args and **kwargs       -> 1 2 (3, 4) {'x': 7, 'y': 8}
```
| Type | Meaning |
|---|---|
| Positional | Matched by order |
| Keyword | `name=value`, order irrelevant |
| Default | Uses default if argument omitted |
| `*args` | Any number of positional args → tuple |
| `**kwargs` | Any number of keyword args → dict |

---

## Q.3

### Q.3 (A) [4 Marks]
> Explain any four attributes of a NumPy array with suitable examples.

```python
import numpy as np
a = np.array([[1, 2, 3], [4, 5, 6]])
```
| Attribute | Meaning | Example | Output |
|---|---|---|---|
| `ndim` | Number of dimensions (axes) | `a.ndim` | `2` |
| `shape` | Tuple of size in each dimension (rows, cols) | `a.shape` | `(2, 3)` |
| `size` | Total number of elements | `a.size` | `6` |
| `dtype` | Data type of elements | `a.dtype` | `int64` |
| `itemsize` | Bytes occupied by each element | `a.itemsize` | `8` |
| `nbytes` | Total bytes (size × itemsize) | `a.nbytes` | `48` |
| `T` | Transpose of the array | `a.T` | `[[1 4] [2 5] [3 6]]` |

```python
print(a.ndim, a.shape, a.size, a.dtype)    # 2 (2, 3) 6 int64
print(a.T.shape)                           # (3, 2)
```

---

### Q.3 (B) [3 Marks]
> What are array creation routines in NumPy? Explain any three with examples.
> **OR**
> Write short note on conditional selection in NumPy with an example.

**Array creation routines** are NumPy functions that **create new arrays** (instead of converting lists manually) — filled with constants, sequences, identity matrices or random values.

1. **`np.zeros(shape)`** — array of zeros: `np.zeros((2, 3))` → `[[0. 0. 0.] [0. 0. 0.]]`
2. **`np.arange(start, stop, step)`** — evenly spaced values by step (stop excluded): `np.arange(0, 10, 3)` → `[0 3 6 9]`
3. **`np.linspace(start, stop, num)`** — `num` equally spaced values (stop included): `np.linspace(0, 1, 5)` → `[0. 0.25 0.5 0.75 1.]`

Others: `np.ones`, `np.eye`, `np.full`, `np.empty`, `np.random.rand`. More: **Paper 2 → Q.2 (C)**.
```python
import numpy as np
print(np.zeros((2, 3)))
print(np.arange(0, 10, 3))
print(np.linspace(0, 1, 5))
```

**OR — Conditional selection in NumPy:** selecting elements that satisfy a condition using a **Boolean mask** (details: **Paper 2 → Q.2 (B)**).
```python
import numpy as np
arr = np.array([5, 12, 8, 21, 3, 16])
print(arr > 10)                         # [False  True False  True False  True]
print(arr[arr > 10])                    # [12 21 16]
print(arr[(arr > 5) & (arr < 20)])      # [12  8 16]    (& | ~ with parentheses)
arr[arr < 5] = 0                        # replace selected values
print(np.where(arr % 2 == 0, "even", "odd"))
```

---

### Q.3 (C) [7 Marks]
> Write a Python program using Beautiful Soup to extract all hyperlinks (`<a>` tags with href attributes) from an HTML document. Explain the steps involved.
> **OR**
> Consider the following NumPy array:
> ```python
> arr = np.array([[5, 10, 15, 20], [25, 30, 35, 40], [45, 50, 55, 60], [65, 70, 75, 80]])
> ```
> a) Extract the first two rows. b) Extract the last column of all rows. c) Extract the subarray [[30, 35], [50, 55]]. d) Replace all elements in the second row with 0.

**Steps:**
1. Install and import: `pip install beautifulsoup4 requests`; `from bs4 import BeautifulSoup`.
2. Obtain the HTML (from a local string/file, or download with `requests.get(url).text`).
3. Create a `BeautifulSoup` object with a parser (`"html.parser"` or `"lxml"`).
4. Find all `<a>` tags that have an `href` attribute using `find_all("a", href=True)`.
5. Read the attribute with `tag["href"]` (or `tag.get("href")`) and the link text with `tag.get_text()`.
6. Print/store the links.

```python
from bs4 import BeautifulSoup
import requests

# ---- Option A: HTML document given as string / file ----
html_doc = """
<html><head><title>Sample Page</title></head>
<body>
  <h1>Useful Links</h1>
  <a href="https://www.python.org">Python</a>
  <a href="https://pandas.pydata.org">Pandas</a>
  <a>No href here</a>
  <a href="/about.html">About</a>
</body></html>
"""
# with open("page.html", encoding="utf-8") as f: html_doc = f.read()      # from a file
# html_doc = requests.get("https://example.com").text                      # from the web

soup = BeautifulSoup(html_doc, "html.parser")          # step 3

links = soup.find_all("a", href=True)                  # step 4 (skips <a> without href)
print("Total links:", len(links))
for a in links:
    print(a.get_text(strip=True), "->", a["href"])     # step 5
```
**Output:**
```
Total links: 3
Python -> https://www.python.org
Pandas -> https://pandas.pydata.org
About -> /about.html
```
To collect only the URLs: `urls = [a["href"] for a in soup.find_all("a", href=True)]`. For relative links use `urllib.parse.urljoin(base_url, href)`.

**OR — NumPy indexing and slicing**
```python
import numpy as np
arr = np.array([[ 5, 10, 15, 20],
                [25, 30, 35, 40],
                [45, 50, 55, 60],
                [65, 70, 75, 80]])

# a) First two rows
print(arr[:2])
# [[ 5 10 15 20]
#  [25 30 35 40]]

# b) Last column of all rows
print(arr[:, -1])          # [20 40 60 80]

# c) Subarray [[30, 35], [50, 55]]  -> rows 1-2, columns 1-2
print(arr[1:3, 1:3])
# [[30 35]
#  [50 55]]

# d) Replace all elements in the second row with 0
arr[1] = 0                 # same as arr[1, :] = 0
print(arr)
# [[ 5 10 15 20]
#  [ 0  0  0  0]
#  [45 50 55 60]
#  [65 70 75 80]]
```
Slicing syntax: `arr[row_start:row_stop, col_start:col_stop]`; negative index `-1` = last.

---

## Q.4

### Q.4 (A) [4 Marks]
> Explain how Pandas handles missing data. Discuss dropna(), fillna(), and interpolate() with examples.

Pandas represents missing data as **`NaN`** (Not a Number; `None`/`NaT` are also detected). Detect with `isnull()`/`isna()`, `notnull()`, and count with `df.isnull().sum()`. Handling options: remove (`dropna`), replace (`fillna`), estimate (`interpolate`).

```python
import pandas as pd
import numpy as np
df = pd.DataFrame({'A': [1, np.nan, 3, np.nan, 5],
                   'B': [10, 20, np.nan, 40, 50]})
print(df.isnull().sum())      # A: 2, B: 1
```
**1. `dropna()`** — removes rows/columns containing missing values.
`df.dropna(axis=0, how='any', thresh=None, subset=None)` — `axis=1` for columns, `how='all'` drops only if all NaN, `subset=['A']` checks selected columns.
```python
print(df.dropna())             # rows 0 and 4 only (no NaN)
print(df.dropna(axis=1))       # empty - both columns have NaN
print(df.dropna(subset=['B'])) # drop rows where B is NaN
```
**2. `fillna()`** — replaces NaN with a given value / statistic / method.
```python
print(df.fillna(0))                         # constant
print(df.fillna(df.mean()))                 # column mean: A -> 3.0, B -> 30.0
print(df['A'].fillna(method='ffill'))       # forward fill (use df['A'].ffill())
```
**3. `interpolate()`** — estimates missing values from neighbouring values (default **linear** interpolation); suitable for ordered/time-series data.
```python
print(df['A'].interpolate())   # [1.0, 2.0, 3.0, 4.0, 5.0]
print(df['B'].interpolate())   # [10.0, 20.0, 30.0, 40.0, 50.0]
```

---

### Q.4 (B) [3 Marks]
> Write a short note on setting and resetting index in a Pandas DataFrame.
> **OR**
> What is a Time Series in Pandas? Give an example of creating a simple time series.

**Setting the index — `set_index()`:** makes one or more columns the row index (label), enabling label-based access with `.loc`.
```python
import pandas as pd
df = pd.DataFrame({'RollNo': [1, 2, 3], 'Name': ['A', 'B', 'C'], 'Marks': [80, 90, 70]})
df2 = df.set_index('RollNo')            # RollNo becomes index
print(df2.loc[2])                       # row with RollNo 2
df3 = df.set_index(['RollNo', 'Name'])  # MultiIndex (two columns)
```
Options: `drop=False` keeps the column too, `inplace=True`.

**Resetting the index — `reset_index()`:** moves the index back to a column and restores the default 0,1,2… integer index (`drop=True` discards the old index).
```python
print(df2.reset_index())                # RollNo returns as a column
print(df2.reset_index(drop=True))       # old index thrown away
```
Use after filtering/sorting/groupby to get a clean index. (More: **Paper 4 → Q.4 (B)**.)

**OR — Time series in Pandas:** a series of data points **indexed by time order** (equal intervals e.g. daily, monthly). Pandas provides `Timestamp`, `DatetimeIndex`, `pd.date_range()`, `pd.to_datetime()`, `resample()`, `rolling()`, `shift()`.
```python
import pandas as pd
dates = pd.date_range(start='2025-01-01', periods=5, freq='D')
ts = pd.Series([100, 110, 105, 120, 130], index=dates)
print(ts)
# 2025-01-01    100
# 2025-01-02    110
# 2025-01-03    105
# 2025-01-04    120
# 2025-01-05    130
# Freq: D, dtype: int64
print(ts['2025-01-03'])                 # 105
print(ts.resample('2D').mean())         # aggregate to 2-day periods
print(ts.rolling(3).mean())             # 3-day moving average
```
(More: **Paper 2 → Q.3 (A)**.)

---

### Q.4 (C) [7 Marks]
> Consider the following DataFrame created from a dictionary:
> ```python
> data = {'EmpID': [101, 102, 103, 104, 105],
>         'Name': ['Aarav', 'Diya', 'Karan', 'Meera', 'Sahil'],
>         'Dept': ['HR', 'IT', 'IT', 'Finance', 'HR'],
>         'Salary': [40000, 55000, 60000, 45000, 70000],
>         'Bonus': [5000, None, 8000, None, 10000]}
> df = pd.DataFrame(data)
> ```
> a) Display the names of all employees working in the IT department. b) Find the employees having Salary greater than 50,000. c) Replace all missing values in the Bonus column with 0. d) Group the employees by Department and find the average salary for each department.
> **OR**
> Consider the following DataFrame (RollNo, Name, Math, Science): a) Display the names of all students who scored more than 80 in Math. b) Display only the RollNo and Name columns. c) Add a new column Total which is the sum of Math and Science marks. d) Find the average marks in Science.

```python
import pandas as pd
data = {
    'EmpID': [101, 102, 103, 104, 105],
    'Name': ['Aarav', 'Diya', 'Karan', 'Meera', 'Sahil'],
    'Dept': ['HR', 'IT', 'IT', 'Finance', 'HR'],
    'Salary': [40000, 55000, 60000, 45000, 70000],
    'Bonus': [5000, None, 8000, None, 10000]
}
df = pd.DataFrame(data)

# a) Names of employees in IT department
print(df[df['Dept'] == 'IT']['Name'])
# 1    Diya
# 2    Karan

# b) Employees with Salary > 50000
print(df[df['Salary'] > 50000])
#    EmpID   Name Dept  Salary    Bonus
# 1    102   Diya   IT   55000      NaN
# 2    103  Karan   IT   60000   8000.0
# 4    105  Sahil   HR   70000  10000.0

# c) Replace missing Bonus values with 0
df['Bonus'] = df['Bonus'].fillna(0)
print(df['Bonus'].tolist())            # [5000.0, 0.0, 8000.0, 0.0, 10000.0]

# d) Average salary per department
print(df.groupby('Dept')['Salary'].mean())
# Dept
# Finance    45000.0
# HR         55000.0
# IT         57500.0
```
Check: HR = (40000+70000)/2 = 55000; IT = (55000+60000)/2 = 57500; Finance = 45000.

**OR — Students DataFrame**
```python
import pandas as pd
data = {
    'RollNo': [1, 2, 3, 4, 5],
    'Name': ['Aarav', 'Diya', 'Karan', 'Meera', 'Sahil'],
    'Math': [78, 85, 92, 67, 80],
    'Science': [88, 79, 95, 70, 85]
}
df = pd.DataFrame(data)

# a) Students who scored more than 80 in Math
print(df[df['Math'] > 80]['Name'])
# 1    Diya      (85)
# 2    Karan     (92)        # Sahil scored exactly 80 -> not included

# b) Only RollNo and Name columns
print(df[['RollNo', 'Name']])

# c) Add Total column
df['Total'] = df['Math'] + df['Science']
print(df)
#    RollNo   Name  Math  Science  Total
# 0       1  Aarav    78       88    166
# 1       2   Diya    85       79    164
# 2       3  Karan    92       95    187
# 3       4  Meera    67       70    137
# 4       5  Sahil    80       85    165

# d) Average marks in Science
print(df['Science'].mean())            # (88+79+95+70+85)/5 = 417/5 = 83.4
```

---

## Q.5

### Q.5 (A) [4 Marks]
> What are gridlines and ticks in a plot? Write commands to enable gridlines and customize tick marks in a Matplotlib chart.

- **Ticks:** small marks on the x/y axis indicating the **position of data values**, with **tick labels** (numbers/text) beside them. *Major ticks* are labelled; *minor ticks* are smaller intermediate marks.
- **Gridlines:** horizontal/vertical lines drawn **across the plot area from the tick positions** to help read values accurately.

**Commands:**
```python
import matplotlib.pyplot as plt
import numpy as np
from matplotlib.ticker import MultipleLocator

x = np.arange(1, 11)
y = x ** 2
fig, ax = plt.subplots()
ax.plot(x, y, marker='o')

# Enable gridlines
ax.grid(True)                                              # simple grid (plt.grid(True))
ax.grid(True, which='major', axis='both', linestyle='--', color='gray', linewidth=0.7, alpha=0.7)
ax.grid(True, axis='y')                                    # only horizontal lines

# Customise ticks
ax.set_xticks([2, 4, 6, 8, 10])                            # tick positions   (plt.xticks)
ax.set_xticklabels(['Two', 'Four', 'Six', 'Eight', 'Ten']) # tick labels
ax.set_yticks(range(0, 101, 20))
ax.tick_params(axis='both', which='major', direction='in', length=7, width=2,
               color='red', labelsize=10, labelcolor='blue')   # style
ax.xaxis.set_minor_locator(MultipleLocator(1))             # minor ticks
ax.tick_params(which='minor', length=3)
plt.show()
```
`plt.minorticks_on()` enables minor ticks; `plt.xticks(rotation=45)` rotates labels.

---

### Q.5 (B) [3 Marks]
> Write Python code to plot a boxplot for the dataset: `scores = [55, 67, 89, 45, 78, 90, 100, 60]`. Label the y-axis as "Marks" and give the plot a title "Student Scores".
> **OR**
> Write Python code to plot a histogram for the following dataset using 5 bins: `Ages = [18, 22, 25, 19, 30, 27, 24, 21, 20, 23, 26]`. Include axis labels and title.

```python
import matplotlib.pyplot as plt

scores = [55, 67, 89, 45, 78, 90, 100, 60]

plt.boxplot(scores)
plt.ylabel("Marks")
plt.title("Student Scores")
plt.show()
```
**Interpretation (sorted data: 45, 55, 60, 67, 78, 89, 90, 100):** minimum = 45, maximum = 100, median = (67+78)/2 = **72.5**, Q1 ≈ 57.5, Q3 ≈ 89.5. The box spans Q1–Q3, the orange line marks the median and the whiskers reach the min and max (no outliers).

**OR — Histogram (5 bins):**
```python
import matplotlib.pyplot as plt

Ages = [18, 22, 25, 19, 30, 27, 24, 21, 20, 23, 26]

plt.hist(Ages, bins=5, color='skyblue', edgecolor='black')
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.title("Histogram of Ages")
plt.show()
```
Range 18–30 divided into 5 bins of width 2.4: [18–20.4) → 18, 19, 20 (3); [20.4–22.8) → 21, 22 (2); [22.8–25.2) → 23, 24, 25 (3); [25.2–27.6) → 26, 27 (2); [27.6–30] → 30 (1). A histogram shows the **frequency distribution** of continuous data (bars touch each other).

---

### Q.5 (C) [7 Marks]
> Write a Python program to plot the marks of 5 students in two subjects (Math and Science) on the same line chart using matplotlib with different line styles, colors, and markers. Add axis labels, title, legend, and annotation to highlight the highest mark. Export the graph to a PDF file.
> **OR**
> Write a Python program to plot a bar chart using matplotlib showing sales of 5 products. Display the value of each bar on top, add axis labels, title, and custom colors for each bar. Export the chart as a PNG image.

```python
import matplotlib.pyplot as plt

students = ['Aarav', 'Diya', 'Karan', 'Meera', 'Sahil']
math     = [78, 85, 92, 67, 80]
science  = [88, 79, 95, 70, 85]

plt.figure(figsize=(8, 5))

# Different line styles, colours and markers
plt.plot(students, math,    color='blue',  linestyle='-',  linewidth=2, marker='o', label='Math')
plt.plot(students, science, color='green', linestyle='--', linewidth=2, marker='s', label='Science')

# Axis labels, title, legend, grid
plt.xlabel('Students')
plt.ylabel('Marks')
plt.title('Marks of Students in Math and Science')
plt.legend(loc='lower left')
plt.grid(True, linestyle=':', alpha=0.6)

# Annotation to highlight the highest mark (Science = 95 for Karan)
highest = max(max(math), max(science))                       # 95
subject = science if highest in science else math
idx = subject.index(highest)
plt.annotate(f'Highest: {highest}', xy=(students[idx], highest),
             xytext=(idx - 1.2, highest + 2),
             arrowprops=dict(facecolor='red', arrowstyle='->'),
             fontsize=10, color='red')

plt.ylim(60, 102)
plt.tight_layout()

# Export to PDF (save BEFORE plt.show())
plt.savefig('student_marks.pdf', format='pdf')
plt.show()
```
**Explanation:** `marker`, `linestyle`, `color` differentiate the two lines; `label` + `plt.legend()` gives the legend; `plt.annotate()` highlights the maximum mark (95, Karan, Science); `plt.savefig('file.pdf')` exports the figure — call it **before `plt.show()`**, otherwise a blank file may be saved.

**OR — Bar chart with values on top, custom colours, export as PNG**
```python
import matplotlib.pyplot as plt

products = ['Laptop', 'Mobile', 'Tablet', 'Watch', 'Camera']
sales    = [120, 250, 90, 150, 70]
colors   = ['#1f77b4', '#ff7f0e', '#2ca02c', '#d62728', '#9467bd']   # custom colour per bar

plt.figure(figsize=(8, 5))
bars = plt.bar(products, sales, color=colors, edgecolor='black')

# Display the value of each bar on top
for bar in bars:
    h = bar.get_height()
    plt.text(bar.get_x() + bar.get_width() / 2, h + 3, str(h),
             ha='center', va='bottom', fontweight='bold')
# (Matplotlib >= 3.4 alternative: plt.bar_label(bars))

plt.xlabel('Products')
plt.ylabel('Sales (units)')
plt.title('Sales of 5 Products')
plt.ylim(0, 290)
plt.tight_layout()

plt.savefig('product_sales.png', dpi=300)     # export as PNG
plt.show()
```
`plt.bar(x, height, color=[...])` draws bars; `plt.text()` (or `plt.bar_label()`) writes the value above every bar; `plt.savefig('name.png', dpi=300)` exports a high-resolution image.

---

**END OF DOCUMENT** — Best of luck for your exams!
