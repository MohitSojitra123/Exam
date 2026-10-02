# 🐍📊 Python for Data Science — Complete Exam Solutions 🎓

> 🧑‍🎓 **Exam-oriented answers** (Definition → Explanation → Example → Output → Key Points)
> 😎 *"Don't panic, just import pandas as pd!"* 🐼
> ✅ Every question from Units 1–5 is solved. Repeated questions (they appear in several papers) are solved **once** and cross-referenced with 🔁.

---

## 🗺️ Quick Index

| Unit | Topics |
|------|--------|
| 🟢 Unit 1 | Python basics, data types, operators, loops, magic commands, pipeline, NumPy intro |
| 🔵 Unit 2 | Strings, functions, collections, Pandas join/merge, NetworkX, Seaborn, scraping, MySQL, loops |
| 🟣 Unit 3 | NumPy attributes/indexing, Pandas programs (Restaurant & Salaries), MultiIndex, Matplotlib basics |
| 🟠 Unit 4 | Missing data, Series/DataFrame, Scikit-learn, Clustering, EDA, Seaborn, NetworkX |
| 🔴 Unit 5 | Matplotlib programs, TF-IDF, BoW, ML (Regression, KNN, Logistic, K-Means), graph drawing |

**Legend:** 📝 Theory | 💻 Code | 📤 Output | 🎯 Exam Tip | 🤣 Fun Note

---
---

# 🟢 UNIT 1 — Python Fundamentals & Data Science Basics

---

## 🔹 Q1(A) — List any four advantages of Python over other programming languages (4 marks)

📝 **Answer:**

| # | Advantage | Explanation |
|---|-----------|-------------|
| 1️⃣ | **Simple & Easy to Learn** 🍼 | Syntax is close to English; no semicolons or curly braces. `print("Hi")` is a full program (Java needs a class + main method!). |
| 2️⃣ | **Interpreted Language** ⚡ | Code runs line by line, no separate compilation. Debugging is easy. |
| 3️⃣ | **Rich Libraries** 📚 | NumPy, Pandas, Matplotlib, Scikit-learn, TensorFlow, Django, Flask. |
| 4️⃣ | **Cross-Platform & Open Source** 🌍 | Same code runs on Windows, Linux, macOS. Free to use. |
| 5️⃣ | Dynamically typed, large community 👥 | No need to declare variable types; huge help available online. |

💻 **Example – Python vs Java:**
```python
# Python
print("Hello, World!")
```
```java
// Java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
🤣 *Python: 1 line. Java: "Hold my coffee, I need 5 lines." ☕*

---

## 🔹 Q1(B) — Difference between Identity and Membership operators (3 marks)

📝 **Identity operators** check whether two variables refer to the **same object in memory** (`is`, `is not`).
**Membership operators** check whether a value **exists inside a sequence** such as list, tuple, string, set, dict (`in`, `not in`).

| Feature | Identity (`is`, `is not`) 🪪 | Membership (`in`, `not in`) 🧺 |
|---------|-----------------------------|--------------------------------|
| Purpose | Same memory object? | Present in a sequence? |
| Compares | Memory address (`id()`) | Elements of container |
| Operands | Any two objects | Value and a container |
| Returns | True / False | True / False |

💻 **Examples:**
```python
# Identity
a = [1, 2, 3]
b = a            # same object
c = [1, 2, 3]    # equal but different object
print(a is b)    # True
print(a is c)    # False  (different objects)
print(a == c)    # True   (values equal)
print(a is not c)# True

# Membership
fruits = ["apple", "banana", "mango"]
print("apple" in fruits)       # True
print("grapes" not in fruits)  # True
print("a" in "python")         # False
```
🎯 **Tip:** `==` compares **values**, `is` compares **identity**.

---

## 🔹 Q1(B) OR — What are Magic Commands? Give any two examples (3 marks)

📝 **Magic commands** are special commands in **IPython/Jupyter Notebook** that start with `%` (line magic) or `%%` (cell magic). They give extra functionality such as timing code, running scripts, listing variables, etc. 🪄

| Type | Symbol | Works on |
|------|--------|----------|
| Line magic | `%` | Single line |
| Cell magic | `%%` | Entire cell |

💻 **Two examples:**
```python
# 1. %timeit  -> measures execution time
%timeit sum(range(1000))
# 📤 4.5 µs ± 100 ns per loop

# 2. %matplotlib inline -> shows plots inside notebook
%matplotlib inline
import matplotlib.pyplot as plt
plt.plot([1,2,3],[4,5,6])
```
Others: `%run`, `%who`, `%reset`, `%time`, `%pwd`, `%lsmagic`. ✨

---

## 🔹 Q1(C) — What is Datatype? List Python datatypes with example (7 marks)

📝 **Definition:** A **data type** specifies the **kind of value** a variable holds and the operations allowed on it. Python is **dynamically typed** — type is decided at runtime. Use `type()` to check it.

### 🗂️ Classification of Python Data Types
```
Python Data Types
├── 🔢 Numeric  : int, float, complex
├── 🔤 Text     : str
├── 📦 Sequence : list, tuple, range
├── 🗝️ Mapping  : dict
├── 🧺 Set      : set, frozenset
├── ✅ Boolean  : bool
├── 🚫 None     : NoneType
└── 💾 Binary   : bytes, bytearray
```

| Data Type | Description | Mutable? | Example |
|-----------|-------------|----------|---------|
| `int` | Whole numbers | ❌ | `x = 10` |
| `float` | Decimal numbers | ❌ | `y = 3.14` |
| `complex` | Real + imaginary | ❌ | `z = 2+3j` |
| `str` | Text | ❌ | `s = "Python"` |
| `list` | Ordered, changeable | ✅ | `[1, 2, "a"]` |
| `tuple` | Ordered, fixed | ❌ | `(1, 2, 3)` |
| `range` | Sequence of numbers | ❌ | `range(5)` |
| `dict` | Key–value pairs | ✅ | `{"name":"Raj"}` |
| `set` | Unordered, unique | ✅ | `{1, 2, 3}` |
| `bool` | True/False | ❌ | `True` |
| `NoneType` | No value | ❌ | `None` |

💻 **Program:**
```python
a = 10;            print(type(a))   # <class 'int'>
b = 3.14;          print(type(b))   # <class 'float'>
c = 2 + 3j;        print(type(c))   # <class 'complex'>
d = "Hello";       print(type(d))   # <class 'str'>
e = [1, 2, 3];     print(type(e))   # <class 'list'>
f = (1, 2, 3);     print(type(f))   # <class 'tuple'>
g = {"id": 1};     print(type(g))   # <class 'dict'>
h = {1, 2, 3};     print(type(h))   # <class 'set'>
i = True;          print(type(i))   # <class 'bool'>
j = None;          print(type(j))   # <class 'NoneType'>
```
🎯 **Tip:** Mention *mutable vs immutable* — examiners love it. 😉

---

## 🔹 Q1(C) OR — break, continue and pass keywords (7 marks)

📝 These are **loop control statements**.

| Keyword | Effect | Emoji |
|---------|--------|-------|
| `break` | **Terminates** the loop immediately | 🛑 |
| `continue` | **Skips** the current iteration, goes to the next | ⏭️ |
| `pass` | **Does nothing** (placeholder) | 🫥 |

### 🛑 `break`
```python
for i in range(1, 10):
    if i == 5:
        break
    print(i, end=" ")
# 📤 1 2 3 4
```
### ⏭️ `continue`
```python
for i in range(1, 6):
    if i == 3:
        continue
    print(i, end=" ")
# 📤 1 2 4 5   (3 skipped)
```
### 🫥 `pass`
```python
for i in range(1, 6):
    if i == 3:
        pass        # nothing happens, loop continues normally
    print(i, end=" ")
# 📤 1 2 3 4 5

def future_function():
    pass            # avoids syntax error for empty body
```
**Flow diagram:**
```
Loop start ─► condition ─► break?    ──► EXIT loop 🛑
                       └─► continue? ──► next iteration ⏭️
                       └─► pass?     ──► run next statement 🫥
```
🤣 *`pass` is like a student in a lecture: physically present, mentally absent.*

---

## 🔹 Q1(A) (Paper 2) — List and explain steps of Data Science Pipeline (4 marks)
## 🔹 Q1(A) (Paper 4) — Explain Data Science Pipeline in detail (4 marks) 🔁

📝 **Definition:** A **Data Science Pipeline** is the sequence of steps used to convert **raw data into useful insights/decisions**.

```
 📥 Data      🧹 Data       🔍 Exploratory   🤖 Modeling     📈 Evaluation   🚀 Deployment &
Collection → Cleaning  →  Data Analysis →  (ML Algos)  →  & Validation →  Communication
```

| Step | Explanation |
|------|-------------|
| 1️⃣ **Problem Definition** 🎯 | Understand business goal and what to predict. |
| 2️⃣ **Data Collection** 📥 | Gather data from CSV, databases, APIs, web scraping, sensors. |
| 3️⃣ **Data Cleaning / Preparation** 🧹 | Handle missing values, duplicates, outliers, wrong types; ~70-80% of the time is spent here! |
| 4️⃣ **Exploratory Data Analysis (EDA)** 🔍 | Summary statistics, visualization, correlations, patterns. |
| 5️⃣ **Feature Engineering** 🛠️ | Create/select/scale features, encode categories. |
| 6️⃣ **Model Building** 🤖 | Train ML algorithms (regression, classification, clustering). |
| 7️⃣ **Model Evaluation** 📊 | Accuracy, precision, recall, RMSE, confusion matrix; cross-validation. |
| 8️⃣ **Deployment & Communication** 🚀 | Put model into production; present results using dashboards/reports. |

💻 **Mini example:**
```python
import pandas as pd
from sklearn.linear_model import LinearRegression

df = pd.read_csv("house.csv")            # collect
df = df.dropna()                          # clean
print(df.describe())                      # EDA
X, y = df[["area"]], df["price"]          # features
model = LinearRegression().fit(X, y)      # model
print(model.score(X, y))                  # evaluate
```
🤣 *Data scientist's life: 80% cleaning data, 20% complaining about cleaning data.* 🧽

---

## 🔹 Q1(B) (Paper 2) — Explain `%timeit` with example (3 marks)

📝 `%timeit` is a **magic command** that measures the **execution time** of a statement by running it **many times** and reporting the average (mean ± std. dev.). It chooses the number of loops automatically, so it is more reliable than `%time`.

**Syntax:** `%timeit [options] statement`
Options: `-n` (loops per run), `-r` (number of repeats).
`%%timeit` → times the whole cell.

💻 **Example:**
```python
%timeit [i**2 for i in range(1000)]
# 📤 82.5 µs ± 1.2 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)

%timeit -n 100 -r 3 sum(range(10000))
```
**Cell magic:**
```python
%%timeit
total = 0
for i in range(1000):
    total += i
```
🎯 Use it to **compare** two approaches (list comprehension vs loop) ⏱️.

## 🔹 Q1(B) OR — Explain `%run` with example (3 marks)

📝 `%run` **executes an external Python script (.py) or notebook** inside the current Jupyter session. Variables/functions defined in the script become available in the notebook afterwards.

**Syntax:** `%run filename.py [args]`

💻 **Example:** create `hello.py`
```python
# hello.py
name = "Data Science"
def greet():
    print("Welcome to", name)
```
In notebook:
```python
%run hello.py
greet()
# 📤 Welcome to Data Science
print(name)     # 📤 Data Science
```
Options: `%run -t script.py` (time), `%run -i` (use current namespace).

---

## 🔹 Q1(C) (Paper 2) — What is NumPy? Explain arange, zeros, ones, eye, linspace, rand, randint (7 marks)

📝 **NumPy (Numerical Python)** is a core library for **fast numerical computing**. It provides the **ndarray** (n-dimensional array), vectorized operations, broadcasting, linear algebra, random numbers. NumPy arrays are **faster & use less memory** than Python lists. ⚡

```python
import numpy as np
```

| Function | Purpose | Example | Output |
|----------|---------|---------|--------|
| `np.arange(start, stop, step)` | Evenly spaced values by **step** | `np.arange(0, 10, 2)` | `[0 2 4 6 8]` |
| `np.zeros(shape)` | Array of **0s** | `np.zeros((2,3))` | `[[0. 0. 0.] [0. 0. 0.]]` |
| `np.ones(shape)` | Array of **1s** | `np.ones((2,2))` | `[[1. 1.] [1. 1.]]` |
| `np.eye(n)` | **Identity matrix** | `np.eye(3)` | `[[1. 0. 0.] [0. 1. 0.] [0. 0. 1.]]` |
| `np.linspace(start, stop, num)` | **n equally spaced** points (stop included) | `np.linspace(0, 1, 5)` | `[0. 0.25 0.5 0.75 1.]` |
| `np.random.rand(d0,d1)` | Random floats in **[0,1)** uniform | `np.random.rand(2,2)` | `[[0.37 0.95] [0.73 0.60]]` |
| `np.random.randint(low, high, size)` | Random **integers** in [low, high) | `np.random.randint(1, 10, 5)` | `[3 7 2 9 5]` |

💻 **Full program:**
```python
import numpy as np
print(np.arange(1, 10, 3))          # [1 4 7]
print(np.zeros((2, 3)))
print(np.ones((2, 2)))
print(np.eye(3))
print(np.linspace(0, 10, 5))        # [ 0.   2.5  5.   7.5 10. ]
print(np.random.rand(2, 3))
print(np.random.randint(10, 50, 4))
```
🎯 `arange` → you give the **step**; `linspace` → you give **number of points**.

## 🔹 Q1(C) OR — Conditional selection with DataFrame (7 marks)

📝 **Conditional (Boolean) selection** filters rows of a DataFrame using a **condition that returns True/False**; only rows with `True` are returned.

💻 **Example:**
```python
import pandas as pd
df = pd.DataFrame({
    "Name":  ["Aarav", "Diya", "Karan", "Meera"],
    "Age":   [21, 22, 20, 23],
    "Marks": [78, 85, 92, 67]
})

print(df["Marks"] > 80)          # Boolean Series: F, T, T, F
print(df[df["Marks"] > 80])      # single condition
```
📤
```
    Name  Age  Marks
1   Diya   22     85
2  Karan   20     92
```
**Multiple conditions** — use `&` (and), `|` (or), `~` (not) with **parentheses**:
```python
print(df[(df["Marks"] > 70) & (df["Age"] < 23)])
print(df[(df["Name"] == "Diya") | (df["Marks"] > 90)])
print(df[df["Name"].isin(["Aarav", "Meera"])])
```
Select specific columns: `df[df["Marks"] > 80][["Name","Marks"]]`
Using `.loc`: `df.loc[df["Marks"] > 80, ["Name"]]`
⚠️ Don't use `and`/`or` — use `&`/`|`!

---

## 🔹 Q1(A) (Paper 3) — Different coding styles in Python (4 marks)

📝 Python supports multiple **programming paradigms/styles**:

| Style | Idea | Example |
|-------|------|---------|
| 1️⃣ **Imperative / Procedural** 📜 | Step-by-step instructions that change state | loops, functions |
| 2️⃣ **Object-Oriented (OOP)** 🧱 | Code organised into classes & objects | `class Car:` |
| 3️⃣ **Functional** 🧮 | Uses pure functions, `map`, `filter`, `lambda`, no state change | `map(lambda x: x*2, lst)` |
| 4️⃣ **Declarative** 🗣️ | Say *what* you want, not *how* | list comprehension, SQL-like pandas |

💻 **Same task (square numbers), different styles:**
```python
nums = [1, 2, 3, 4]

# Imperative
res = []
for n in nums:
    res.append(n * n)

# Functional
res = list(map(lambda n: n * n, nums))

# Declarative (comprehension)
res = [n * n for n in nums]

# OOP
class Squarer:
    def __init__(self, data): self.data = data
    def square(self): return [d*d for d in self.data]
print(Squarer(nums).square())     # [1, 4, 9, 16]
```

---

## 🔹 Q1(B) (Paper 3) — Factors that control speed of execution for Data Science applications (3 marks)

📝 Key factors: 🏎️

1. **Hardware** 🖥️ — CPU speed, number of cores, RAM size, GPU/TPU, SSD vs HDD.
2. **Algorithm & Data Structure choice** 🧠 — O(n) vs O(n²); using `set`/`dict` for fast lookup.
3. **Vectorization** ➗ — NumPy/Pandas vector ops are far faster than Python loops (C backend).
4. **Data size & format** 📦 — Parquet/HDF5 faster than CSV; correct dtypes (`float32` vs `float64`).
5. **Parallelism / Multiprocessing** 🔀 — joblib, multiprocessing, Dask, Spark.
6. **Interpreter & compiling tools** ⚙️ — Numba, Cython, PyPy, JIT compilation.
7. **I/O & Memory management** 💾 — chunked reading, caching, avoiding unneeded copies.
8. **Code quality** — efficient libraries, avoiding global variables, profiling (`%timeit`).

💻 Example (vectorization):
```python
import numpy as np
a = np.arange(1_000_000)
%timeit [x*2 for x in a]   # slow  (~100 ms)
%timeit a*2                # fast  (~1 ms)  🚀
```

## 🔹 Q1(B) OR (Paper 3) — Differences between conda and pip

| Feature | **conda** 🐍 | **pip** 📦 |
|---------|-------------|-----------|
| Full form | Conda package & environment manager (Anaconda) | Pip Installs Packages |
| Language support | Any language (Python, R, C libs) | Python packages only |
| Source | Anaconda repositories (conda-forge) | PyPI |
| Environment mgmt | ✅ Built-in (`conda create -n env`) | ❌ Needs `venv`/`virtualenv` |
| Dependency solving | Full dependency resolver incl. binaries | Installs Python deps only |
| Non-Python deps | Handles (e.g., HDF5, MKL) | Cannot |
| Install cmd | `conda install numpy` | `pip install numpy` |
| Package format | `.conda` / `.tar.bz2` binaries | wheels (`.whl`) / source |

```bash
conda create -n ds_env python=3.11
conda activate ds_env
conda install pandas
pip install seaborn
```

---

## 🔹 Q1(C) (Paper 3) — List and explain any seven magic commands with example (7 marks)

| # | Command | Purpose | Example |
|---|---------|---------|---------|
| 1 | `%lsmagic` 📜 | List all magic commands | `%lsmagic` |
| 2 | `%run` 🏃 | Run external script | `%run test.py` |
| 3 | `%time` ⏱️ | Time of single statement | `%time sum(range(10**6))` |
| 4 | `%timeit` 🔁 | Avg time over many runs | `%timeit sum(range(1000))` |
| 5 | `%who` / `%whos` 👀 | List variables (with details) | `%whos` |
| 6 | `%reset` 🧹 | Delete all variables | `%reset -f` |
| 7 | `%matplotlib inline` 📈 | Show plots inside notebook | `%matplotlib inline` |
| 8 | `%pwd` / `%cd` 📂 | Current / change directory | `%pwd` |
| 9 | `%%writefile` ✍️ | Write cell to file | `%%writefile a.py` |
| 10 | `%history` 📖 | Show command history | `%history -n` |
| 11 | `%load` 📥 | Load code from file into cell | `%load a.py` |
| 12 | `%%html`, `%%bash`, `%%time` | Cell magics | `%%bash` + `ls` |

💻 **Demo:**
```python
x = 10
y = "hello"
%who
# 📤 x   y
%whos
# Variable  Type  Data/Info
# x         int   10
# y         str   hello
%%writefile hello.py
print("Hello from file")
%run hello.py
# 📤 Hello from file
%reset -f     # all variables deleted
```

## 🔹 Q1(C) OR (Paper 3) & Q1(C) (Paper 4) — Python Ecosystem for Data Science 🔁 (7 marks)

📝 The **Python ecosystem** is the collection of **libraries, tools and environments** that make Python the most popular language for data science. 🌳

```
                       🐍 PYTHON ECOSYSTEM
 ┌──────────────┬───────────────┬────────────────┬───────────────┬──────────────┐
 │ Numerical    │ Data handling │ Visualization  │ Machine Learn │ Web / DB     │
 │ NumPy, SciPy │ Pandas        │ Matplotlib     │ Scikit-learn  │ BeautifulSoup│
 │              │               │ Seaborn,Plotly │ TensorFlow    │ SQLAlchemy   │
 │              │               │                │ Keras,PyTorch │ Requests     │
 └──────────────┴───────────────┴────────────────┴───────────────┴──────────────┘
          🧪 IDEs: Jupyter, Anaconda, Spyder, VS Code, Google Colab
```

| Category | Tool | Use |
|----------|------|-----|
| Numerical 🔢 | **NumPy** | n-d arrays, math ops |
| Scientific 🔬 | **SciPy** | optimization, statistics, signal |
| Data analysis 🐼 | **Pandas** | Series, DataFrame, cleaning |
| Visualization 🎨 | **Matplotlib, Seaborn, Plotly** | charts |
| Machine Learning 🤖 | **Scikit-learn** | regression, classification, clustering |
| Deep Learning 🧠 | **TensorFlow, Keras, PyTorch** | neural networks |
| NLP 💬 | **NLTK, spaCy** | text processing |
| Graph 🕸️ | **NetworkX** | network analysis |
| Web scraping 🌐 | **BeautifulSoup, Scrapy, Requests** | collecting data |
| Environment 🧰 | **Jupyter, Anaconda, conda, pip** | coding & package mgmt |

**Why this ecosystem is great?** Open-source, large community, easy integration, free, good documentation.

---

## 🔹 Q1(A) (Paper 4 / Python's role) — Explain Python's role in Data Science (3 marks)

📝 Python is the **#1 language for data science** because:

1. 🍼 **Easy syntax** — focus on data, not on code complexity.
2. 📚 **Powerful libraries** — NumPy, Pandas, Matplotlib, Scikit-learn.
3. 🌍 **Community & open source** — tutorials, Stack Overflow, free.
4. 🔗 **Integration** — works with SQL, Hadoop, Spark, C/C++, Excel, web.
5. 🧪 **Notebook support** — Jupyter for interactive analysis & reporting.
6. 🤖 **ML/AI-ready** — TensorFlow, PyTorch, Scikit-learn.
7. 📈 **Visualization** — easy to create charts and dashboards.

Used in: data cleaning, EDA, ML modelling, deep learning, NLP, big-data processing, automation.

## 🔹 OR — Functional and Imperative coding styles in Python (3 marks)

| Feature | **Imperative** 📜 | **Functional** 🧮 |
|---------|------------------|-------------------|
| Focus | *How* to do task, step by step | *What* to compute, using functions |
| State | Changes variables (mutable state) | Avoids side-effects, uses immutability |
| Constructs | `for`, `while`, `if`, assignment | `map`, `filter`, `reduce`, `lambda`, recursion |
| Example | loops with accumulators | expression-based |

```python
nums = [1, 2, 3, 4, 5, 6]

# Imperative: sum of squares of even numbers
total = 0
for n in nums:
    if n % 2 == 0:
        total += n * n
print(total)         # 56

# Functional
from functools import reduce
total = reduce(lambda a, b: a + b,
               map(lambda n: n*n,
                   filter(lambda n: n % 2 == 0, nums)))
print(total)         # 56
```

---

## 🔹 Q1(C) (Paper 4) OR — Explain `%run`, `%time`, `%timeit` and `%reset` (7 marks)

| Magic | Description | Example |
|-------|-------------|---------|
| `%run` 🏃 | Executes an external `.py`/.ipynb in the notebook | `%run prog.py` |
| `%time` ⏱️ | Runs statement **once**, shows CPU time & wall time | `%time sum(range(10**6))` |
| `%timeit` 🔁 | Runs statement **many times**, gives mean±std | `%timeit sum(range(1000))` |
| `%reset` 🧹 | Clears all variables from namespace (`-f` = no confirmation) | `%reset -f` |

💻
```python
%time total = sum(range(10**6))
# 📤 CPU times: user 25 ms, sys: 0 ns, total: 25 ms
#    Wall time: 26 ms

%timeit total = sum(range(10**6))
# 📤 24.1 ms ± 300 µs per loop (mean ± std. dev. of 7 runs, 10 loops each)

a = 5; b = 10
%reset -f
print(a)        # ❌ NameError: name 'a' is not defined
```
**Difference:** `%time` = one run (can vary); `%timeit` = many runs (accurate average).

---

## 🔹 Q1(A) (Paper 5) — Enumerate the list and its methods with example (4 marks)

📝 A **list** is an **ordered, mutable** collection of items written in `[ ]`; allows duplicates and mixed types.

```python
lst = [10, 20, 30]
print(lst[0], lst[-1])    # 10 30
```

| Method | Purpose | Example | Result |
|--------|---------|---------|--------|
| `append(x)` | Add at end | `lst.append(40)` | `[10,20,30,40]` |
| `insert(i,x)` | Add at index | `lst.insert(1,15)` | `[10,15,20,30,40]` |
| `extend(iter)` | Add many | `lst.extend([50,60])` | adds 50, 60 |
| `remove(x)` | Remove first x | `lst.remove(15)` | |
| `pop(i)` | Remove & return index (last default) | `lst.pop()` | 60 |
| `index(x)` | Position of x | `lst.index(30)` | 2 |
| `count(x)` | Occurrences | `lst.count(10)` | 1 |
| `sort()` | Ascending sort | `lst.sort()` | |
| `reverse()` | Reverse in place | `lst.reverse()` | |
| `copy()` | Shallow copy | `b = lst.copy()` | |
| `clear()` | Empty list | `lst.clear()` | `[]` |

```python
nums = [5, 2, 8, 1]
nums.append(9);  nums.sort()
print(nums)                # [1, 2, 5, 8, 9]
nums.reverse(); print(nums)# [9, 8, 5, 2, 1]
```

## 🔹 Q1(B) (Paper 5) — Tuple vs Sets 

| Feature | **Tuple** `( )` | **Set** `{ }` |
|---------|-----------------|---------------|
| Ordered | ✅ Yes | ❌ No |
| Mutable | ❌ No | ✅ Yes (add/remove) |
| Duplicates | ✅ Allowed | ❌ Not allowed |
| Indexing | ✅ `t[0]` | ❌ No indexing |
| Elements | Any (hashable or not) | Only hashable (immutable) |
| Speed | Fast iteration | Fast membership test |
| Example | `(1,2,2,3)` | `{1,2,3}` |

## 🔹 Q1(B) OR (Paper 5) — List vs Sets

| Feature | **List** `[ ]` | **Set** `{ }` |
|---------|---------------|---------------|
| Order | Ordered | Unordered |
| Duplicates | Allowed | Not allowed |
| Indexing/slicing | ✅ | ❌ |
| Mutable | ✅ | ✅ |
| Operations | append, sort, etc. | union, intersection, difference |
| Example | `[1,2,2,3]` | `{1,2,3}` |

```python
print(list([1,2,2,3]))   # [1, 2, 2, 3]
print(set([1,2,2,3]))    # {1, 2, 3}
```

## 🔹 Q1(C) (Paper 5) — What is data type? List types with example 🔁
👉 See **Unit 1 Q1(C)** above.

## 🔹 Q1(C) OR (Paper 5) — Explain variable with suitable example (7 marks)

📝 A **variable** is a **named memory location** used to store data. In Python, no declaration needed — it is created when a value is assigned (`=`). A variable is really a **name (label) pointing to an object**. 🏷️

**Rules for naming:**
- Starts with letter or `_` (not digit)
- Only letters, digits, `_`
- Case-sensitive (`age` ≠ `Age`)
- Cannot be a keyword (`class`, `for`, …)

```python
name = "Raj"          # str
age = 20              # int
height = 5.9          # float
is_student = True     # bool

# multiple assignment
a, b, c = 1, 2, 3
x = y = z = 100

# type can change (dynamic typing)
v = 10
v = "ten"
print(type(v))        # <class 'str'>

# swap
a, b = b, a
print(id(a))          # memory address
```
**Types of variable (scope):** *Local* (inside function), *Global* (outside), `global` keyword, `nonlocal`.
```python
g = 10
def show():
    l = 5
    print(g, l)
show()    # 10 5
```
🤣 *A variable is like a name tag at a party: "Hello, my name is x and I'm holding 10."* 🎉

---

# 🔵 UNIT 2 — Strings, Functions, Collections, Pandas, Libraries

---

## 🔹 Q2(A) — Four commonly used string methods (4 marks)

📝 A **string** is an immutable sequence of characters. Methods return a **new** string.

| Method | Purpose | Example | Output |
|--------|---------|---------|--------|
| `upper()` / `lower()` 🔠 | Convert case | `"python".upper()` | `PYTHON` |
| `strip()` ✂️ | Remove leading/trailing spaces | `"  hi  ".strip()` | `hi` |
| `replace(old,new)` 🔁 | Replace substring | `"cat".replace("c","b")` | `bat` |
| `split(sep)` 🪓 | Split into list | `"a,b,c".split(",")` | `['a','b','c']` |
| `join(list)` 🔗 | Join list into string | `"-".join(["a","b"])` | `a-b` |
| `find(sub)` 🔎 | Index of substring (-1 if absent) | `"hello".find("l")` | `2` |
| `title()`, `capitalize()`, `startswith()`, `endswith()`, `count()` | | | |

```python
s = "  Data Science  "
print(s.strip().upper())          # DATA SCIENCE
print(s.replace("Data", "Big"))   #   Big Science
print(s.split())                  # ['Data', 'Science']
print("-".join(["2024","01","15"]))# 2024-01-15
```

---

## 🔹 Q2(B) — What is a docstring? How is it useful? (3 marks)

📝 A **docstring** (documentation string) is a **string literal placed as the first statement** of a module, class, or function, enclosed in triple quotes `""" """`. It documents what the code does. It is stored in the `__doc__` attribute and shown by `help()`.

**Usefulness:** 📖 documentation • 🧑‍🤝‍🧑 easier for teams • 🛠️ auto-generated docs (Sphinx) • ℹ️ help in IDEs.

```python
def add(a, b):
    """Return the sum of two numbers.

    Parameters: a (int), b (int)
    Returns: int
    """
    return a + b

print(add.__doc__)
help(add)
```
🎯 Comment (`#`) is ignored by Python; docstring is **retained at runtime**.

## 🔹 Q2(B) OR — Lambda function (3 marks)

📝 A **lambda** is a small **anonymous (nameless) one-line function** created with the `lambda` keyword. It can have any number of arguments but **only one expression**, whose value is returned automatically.

**Syntax:** `lambda arguments : expression`

```python
double = lambda x: x * 2
print(double(5))             # 10

add = lambda a, b: a + b
print(add(3, 4))             # 7

# with map / filter
nums = [1, 2, 3, 4]
print(list(map(lambda x: x*2, nums)))        # [2, 4, 6, 8]
print(list(filter(lambda x: x%2==0, nums)))  # [2, 4]
```

---

## 🔹 Q2(C) — Compare List, Tuple, Set, Dictionary (7 marks)

| Feature | **List** 📋 | **Tuple** 📦 | **Set** 🧺 | **Dictionary** 🗝️ |
|---------|------------|-------------|-----------|------------------|
| Syntax | `[1,2]` | `(1,2)` | `{1,2}` | `{"a":1}` |
| Ordered | ✅ | ✅ | ❌ | ✅ (Py 3.7+ insertion order) |
| Mutable | ✅ | ❌ | ✅ | ✅ |
| Duplicates | ✅ | ✅ | ❌ | Keys ❌, values ✅ |
| Indexing | ✅ index | ✅ index | ❌ | ✅ by key |
| Elements | any | any | hashable only | key–value pairs |
| Speed | medium | faster than list | fast lookup | fast lookup O(1) |
| Use case | collection to modify | fixed data, safe | unique items, set maths | mapping, records |
| Empty creation | `[]` / `list()` | `()` / `tuple()` | `set()` (not `{}`!) | `{}` / `dict()` |

```python
l = [1, 2, 2, 3]            ; l.append(4)
t = (1, 2, 2, 3)            # t[0] = 5  -> TypeError
s = {1, 2, 2, 3}            ; s.add(4)    # {1,2,3,4}
d = {"name": "Raj", "age": 20}; d["city"] = "Rajkot"
print(l, t, s, d, sep="\n")
```
🤣 `{}` creates an empty **dict**, not a set. Python: *"Surprise!"* 🎁

## 🔹 Q2(C) OR — Types of function arguments (7 marks) 🔁 (Also asked in Paper 5)

📝 **Arguments** are values passed to a function. Types:

### 1️⃣ Positional (Required) arguments
Matched **by position**; number must be equal.
```python
def sub(a, b): return a - b
print(sub(10, 4))      # 6
```
### 2️⃣ Keyword arguments
Passed as `name=value`; order doesn't matter.
```python
print(sub(b=4, a=10))  # 6
```
### 3️⃣ Default arguments
Parameter has a default if not supplied.
```python
def greet(name, msg="Hello"):
    print(msg, name)
greet("Raj")             # Hello Raj
greet("Raj", "Hi")       # Hi Raj
```
### 4️⃣ Variable-length positional `*args`
Accepts any number of positional args as a **tuple**.
```python
def total(*args):
    return sum(args)
print(total(1, 2, 3, 4))   # 10
```
### 5️⃣ Variable-length keyword `**kwargs`
Accepts any number of keyword args as a **dict**.
```python
def info(**kwargs):
    for k, v in kwargs.items():
        print(k, "=", v)
info(name="Raj", age=20)
# name = Raj
# age = 20
```
**Order rule:** `positional → *args → default → **kwargs` 🎯

---

## 🔹 Q2(A) (Paper 2) — Compare NumPy and Pandas (4 marks)

| Feature | **NumPy** 🔢 | **Pandas** 🐼 |
|---------|-------------|--------------|
| Main structure | `ndarray` (n-dimensional) | `Series` (1D), `DataFrame` (2D) |
| Data type | **Homogeneous** (one dtype) | **Heterogeneous** (many dtypes) |
| Indexing | Integer position only | Labels + position (`loc`, `iloc`) |
| Missing data | Poor (`np.nan` only for floats) | Excellent (`dropna`, `fillna`) |
| Speed | Faster for numeric ops | Slightly slower, more features |
| Memory | Less | More |
| Best for | Mathematical/matrix computing | Tabular data analysis (CSV, Excel, SQL) |
| File I/O | Limited (`np.loadtxt`) | `read_csv`, `read_excel`, `read_sql` |
| Built on | C | NumPy |

```python
import numpy as np, pandas as pd
a = np.array([[1,2],[3,4]])
df = pd.DataFrame(a, columns=["A","B"], index=["r1","r2"])
```

---

## 🔹 Q2(B) (Paper 2) — Explain `join()` function in Pandas (3 marks)

📝 `DataFrame.join()` combines two DataFrames **based on their index** (by default) — a convenient way to do a **left join** on index.

**Syntax:** `df1.join(df2, how='left', lsuffix='', rsuffix='', on=None)`

`how` = `left` (default), `right`, `inner`, `outer`.

```python
import pandas as pd
df1 = pd.DataFrame({"Name": ["A","B","C"]}, index=[1,2,3])
df2 = pd.DataFrame({"Marks": [80,90,70]}, index=[1,2,4])

print(df1.join(df2))                # left join
print(df1.join(df2, how="inner"))
```
📤 left join:
```
  Name  Marks
1    A   80.0
2    B   90.0
3    C    NaN
```
📤 inner join:
```
  Name  Marks
1    A     80
2    B     90
```
If same column names exist → use `lsuffix="_l", rsuffix="_r"`.

## 🔹 Q2(B) OR — Explain `merge()` function in Pandas (3 marks)

📝 `pd.merge()` combines DataFrames using **common columns (keys)** — like SQL JOIN.

**Syntax:** `pd.merge(left, right, on='key', how='inner')`
`how`: `inner` (default), `left`, `right`, `outer`. Also `left_on`, `right_on`.

```python
emp = pd.DataFrame({"id":[1,2,3], "name":["Aman","Bina","Chirag"]})
sal = pd.DataFrame({"id":[1,2,4], "salary":[30000,40000,50000]})

print(pd.merge(emp, sal, on="id"))                 # inner
print(pd.merge(emp, sal, on="id", how="left"))
print(pd.merge(emp, sal, on="id", how="outer"))
```
📤 inner:
```
   id  name  salary
0   1  Aman   30000
1   2  Bina   40000
```
| how | Result |
|-----|--------|
| inner | only matching keys |
| left | all left + matching right |
| right | all right + matching left |
| outer | all rows from both (NaN where missing) |

---

## 🔹 Q2(C) (Paper 2) — Explain NetworkX library with example (7 marks)

📝 **NetworkX** is a Python library to **create, manipulate and study graphs/networks** (nodes + edges), e.g., social networks, road maps, web links. Install: `pip install networkx`.

**Graph types:** `Graph()` undirected, `DiGraph()` directed, `MultiGraph()`, `MultiDiGraph()`.

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_node("A")
G.add_nodes_from(["B", "C", "D"])
G.add_edge("A", "B")
G.add_edges_from([("B","C"), ("C","D"), ("D","A")])

print("Nodes:", G.nodes())            # ['A','B','C','D']
print("Edges:", G.edges())
print("Degree of A:", G.degree("A"))  # 2
print("Shortest path A->C:", nx.shortest_path(G, "A", "C"))

nx.draw(G, with_labels=True, node_color="lightblue",
        node_size=1000, font_weight="bold")
plt.title("NetworkX Example 🕸️")
plt.show()
```
**Common functions:** `number_of_nodes()`, `number_of_edges()`, `nx.degree_centrality(G)`, `nx.is_connected(G)`, `nx.shortest_path()`.

## 🔹 Q2(C) OR — Different types of graphs in Seaborn (7 marks)

📝 **Seaborn** is a statistical visualization library built on Matplotlib.

| Category | Plot | Function | Use |
|----------|------|----------|-----|
| **Relational** 📈 | Scatter plot | `sns.scatterplot()` | relation of 2 variables |
| | Line plot | `sns.lineplot()` | trend over time |
| **Distribution** 📊 | Histogram | `sns.histplot()` | frequency distribution |
| | KDE plot | `sns.kdeplot()` | smooth density |
| | Rug plot | `sns.rugplot()` | tick marks of data |
| **Categorical** 🗂️ | Bar plot | `sns.barplot()` | mean per category |
| | Count plot | `sns.countplot()` | count of categories |
| | Box plot | `sns.boxplot()` | median, quartiles, outliers |
| | Violin plot | `sns.violinplot()` | distribution + box |
| | Strip/Swarm | `sns.stripplot()`, `swarmplot()` | individual points |
| **Matrix** 🔥 | Heatmap | `sns.heatmap()` | correlation matrix |
| **Regression** 📉 | lmplot / regplot | `sns.lmplot()` | scatter + regression line |
| **Multi-plot** 🧩 | Pairplot | `sns.pairplot()` | all pairwise relationships |
| | Jointplot | `sns.jointplot()` | scatter + histograms |

```python
import seaborn as sns, matplotlib.pyplot as plt
tips = sns.load_dataset("tips")
sns.scatterplot(x="total_bill", y="tip", data=tips)
plt.show()
sns.boxplot(x="day", y="total_bill", data=tips)
plt.show()
sns.heatmap(tips.corr(numeric_only=True), annot=True, cmap="coolwarm")
plt.show()
```

---

## 🔹 Q2(A) (Paper 3) — Web scraping using Beautiful Soup (4 marks)

📝 **Web scraping** = automatically extracting data from websites. **Beautiful Soup (bs4)** parses HTML/XML and provides easy methods to search the parse tree. Used with `requests`.

**Install:** `pip install beautifulsoup4 requests`

**Steps:** 1️⃣ Send HTTP request → 2️⃣ Get HTML → 3️⃣ Parse with BeautifulSoup → 4️⃣ Find tags → 5️⃣ Extract & store data.

```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com"
res = requests.get(url)
soup = BeautifulSoup(res.text, "html.parser")

print(soup.title.text)               # page title
for h in soup.find_all("h2"):        # all <h2>
    print(h.get_text())
for a in soup.find_all("a", href=True):
    print(a["href"])
print(soup.find("p", class_="info"))  # by class
print(soup.select("div.content > p")) # CSS selector
```
Key methods: `find()`, `find_all()`, `select()`, `.text`, `.get('href')`.
⚖️ Respect `robots.txt` and terms of the website.

---

## 🔹 Q2(B) (Paper 3) — Conditional selection in a NumPy array (3 marks) 🔁 (also Paper 4)

📝 **Conditional (Boolean) selection** filters elements of an array using a condition. The condition creates a **Boolean mask**; array[mask] returns elements where True.

```python
import numpy as np
arr = np.array([10, 25, 30, 45, 50])

mask = arr > 30
print(mask)          # [False False False  True  True]
print(arr[mask])     # [45 50]
print(arr[arr > 20]) # [25 30 45 50]

# multiple conditions: & | ~
print(arr[(arr > 20) & (arr < 50)])   # [25 30 45]
print(arr[(arr < 20) | (arr > 45)])   # [10 50]

# Replace values
arr[arr > 40] = 0
print(arr)           # [10 25 30  0  0]

# np.where
print(np.where(arr > 20, "High", "Low"))
```

## 🔹 Q2(B) OR — `rand()`, `randint()`, `randn()` (3 marks)

| Function | Description | Example |
|----------|-------------|---------|
| `np.random.rand(d0,d1..)` 🎲 | **Uniform** random floats in [0,1) | `np.random.rand(2,3)` |
| `np.random.randint(low, high, size)` 🔢 | Random **integers** in [low, high) | `np.random.randint(1,100,5)` |
| `np.random.randn(d0,d1..)` 🔔 | Random floats from **standard normal** distribution (mean 0, SD 1) — can be negative | `np.random.randn(2,2)` |

```python
import numpy as np
print(np.random.rand(2, 2))          # [[0.62 0.11] [0.88 0.34]]
print(np.random.randint(1, 100, 5))  # [45 12 78 3 66]
print(np.random.randn(2, 2))         # [[ 0.45 -1.2 ] [-0.31  1.01]]
np.random.seed(42)                   # reproducible results
```

---

## 🔹 Q2(C) (Paper 3) — NumPy array creation functions with example (7 marks) 🔁

| Function | Purpose | Example |
|----------|---------|---------|
| `np.array()` | From list/tuple | `np.array([1,2,3])` |
| `np.zeros()` | All zeros | `np.zeros((2,3))` |
| `np.ones()` | All ones | `np.ones((2,2))` |
| `np.full()` | Constant value | `np.full((2,2), 7)` |
| `np.empty()` | Uninitialized | `np.empty((2,2))` |
| `np.eye()` / `np.identity()` | Identity matrix | `np.eye(3)` |
| `np.arange()` | By step | `np.arange(0,10,2)` |
| `np.linspace()` | n equally spaced | `np.linspace(0,1,5)` |
| `np.random.rand()` | random | `np.random.rand(2,2)` |
| `np.diag()` | Diagonal matrix | `np.diag([1,2,3])` |

```python
import numpy as np
print(np.array([[1,2,3],[4,5,6]]))
print(np.zeros((2,3)))
print(np.ones((2,2)))
print(np.full((2,2), 9))
print(np.eye(3))
print(np.arange(0, 10, 2))      # [0 2 4 6 8]
print(np.linspace(0, 1, 5))     # [0.   0.25 0.5  0.75 1.  ]
print(np.diag([1, 2, 3]))
```

## 🔹 Q2(C) OR — Cross sections in DataFrame (`xs()`) (7 marks)

📝 `DataFrame.xs()` (**cross-section**) returns a **specific row/column slice** of a DataFrame, especially useful with **MultiIndex** for selecting data at a particular level.

**Syntax:** `df.xs(key, axis=0, level=None, drop_level=True)`

```python
import pandas as pd
idx = pd.MultiIndex.from_tuples(
    [("G1","A"),("G1","B"),("G2","A"),("G2","B")],
    names=["Group","Sub"])
df = pd.DataFrame({"Val":[10,20,30,40]}, index=idx)
print(df)
#            Val
# Group Sub
# G1    A     10
#       B     20
# G2    A     30
#       B     40

print(df.xs("G1"))                  # all rows of Group G1
print(df.xs("A", level="Sub"))      # rows where Sub == "A"
print(df.xs(("G2","B")))            # exact row
```
📤 `df.xs("A", level="Sub")`
```
       Val
Group
G1      10
G2      30
```
With columns: `df.xs("Val", axis=1)`.
Advantage: easier than `.loc` for slicing inner levels.

---

## 🔹 Q2(A) (Paper 4) — Database connectivity with MySQL (4 marks)

📝 Python connects to MySQL using **`mysql-connector-python`** (or `PyMySQL`). Install: `pip install mysql-connector-python`

**Steps:** Import → Connect → Create cursor → Execute query → Fetch/commit → Close.

```python
import mysql.connector

# 1. Connect
con = mysql.connector.connect(
    host="localhost", user="root",
    password="1234", database="college")
cur = con.cursor()                    # 2. cursor

# 3. Create table & insert
cur.execute("CREATE TABLE IF NOT EXISTS student(id INT, name VARCHAR(30))")
cur.execute("INSERT INTO student VALUES (%s, %s)", (1, "Raj"))
con.commit()                          # save changes

# 4. Fetch
cur.execute("SELECT * FROM student")
for row in cur.fetchall():
    print(row)                        # (1, 'Raj')

cur.close(); con.close()              # 5. close
```
Pandas: `pd.read_sql("SELECT * FROM student", con)`.

---

## 🔹 Q2(B) (Paper 4) — `sort()` function of NumPy (3 marks)

📝 `np.sort()` returns a **sorted copy** of an array; `arr.sort()` sorts **in place**. Default axis = -1 (last axis); `kind` = quicksort/mergesort.

```python
import numpy as np
a = np.array([30, 10, 50, 20])
print(np.sort(a))            # [10 20 30 50]
print(np.sort(a)[::-1])      # descending [50 30 20 10]

b = np.array([[3, 1, 2],
              [9, 7, 8]])
print(np.sort(b, axis=1))    # row-wise  [[1 2 3] [7 8 9]]
print(np.sort(b, axis=0))    # column-wise
print(np.argsort(a))         # indices that sort: [1 3 0 2]
```
## 🔹 OR — Conditional selection in numpy array 🔁 → See Q2(B) Paper 3 above.

---

## 🔹 Q2(C) (Paper 4) — `arange`, `zeros`, `ones`, `eye`, `linspace` 🔁 → See Unit 1 Q1(C) NumPy table (all five covered with examples).

## 🔹 Q2(C) OR (Paper 4) — `xs()` and `groupby()` (7 marks)

**`xs()`** 🔁 → see cross-section answer above.

📝 **`groupby()`** splits data into groups based on a column, applies a function (sum, mean, count…), and combines the result (**Split → Apply → Combine**).

```python
import pandas as pd
df = pd.DataFrame({
    "Dept":   ["HR","IT","IT","HR","Fin"],
    "Salary": [40000, 55000, 60000, 45000, 50000]
})
print(df.groupby("Dept")["Salary"].mean())
# Dept
# Fin    50000.0
# HR     42500.0
# IT     57500.0

print(df.groupby("Dept")["Salary"].agg(["sum","mean","max"]))
print(df.groupby("Dept").size())      # count per group
```

---

## 🔹 Q2(A) (Paper 5) — Fibonacci series using recursion (4 marks)

📝 Fibonacci: `0, 1, 1, 2, 3, 5, 8…` → F(n) = F(n-1) + F(n-2); F(0)=0, F(1)=1.

```python
def fib(n):
    if n <= 1:                 # base case
        return n
    return fib(n-1) + fib(n-2) # recursive case

n_terms = int(input("Enter number of terms: "))
if n_terms <= 0:
    print("Enter a positive integer")
else:
    print("Fibonacci series:")
    for i in range(n_terms):
        print(fib(i), end=" ")
```
📤 (n=8) `0 1 1 2 3 5 8 13`

## 🔹 Q2(B) (Paper 5) — For loop statement with example (3 marks)

📝 The `for` loop **iterates over a sequence** (list, tuple, string, range, dict).

**Syntax:** `for variable in sequence:` (+ optional `else`)
```python
for i in range(1, 6):
    print(i, end=" ")            # 1 2 3 4 5

for ch in "Hi":
    print(ch)                    # H i

fruits = ["apple", "mango"]
for f in fruits:
    print(f.upper())

for i in range(3):
    print(i)
else:
    print("Loop finished 🎉")    # runs if no break
```
`range(start, stop, step)`: `range(10, 0, -2)` → 10 8 6 4 2.

## 🔹 Q2(B) OR — While loop statement with example (3 marks)

📝 `while` repeats a block **as long as the condition is True**. Used when number of iterations is unknown.

```python
i = 1
while i <= 5:
    print(i, end=" ")
    i += 1                       # 1 2 3 4 5

# Sum of digits
n, s = 123, 0
while n > 0:
    s += n % 10
    n //= 10
print(s)                         # 6
```
⚠️ Always update the variable, or you get an **infinite loop** ♾️ 🤣 *(your laptop fan will start singing)*.

## 🔹 Q2(C) (Paper 5) — Types of Python function arguments 🔁 → See Q2(C) OR above.

## 🔹 Q2(C) OR (Paper 5) — Program to use nested if statement (7 marks)

📝 A **nested if** is an `if` inside another `if`. Inner condition is checked only if outer is True.

```python
# Largest of three numbers + grade check using nested if
a = int(input("Enter a: "))
b = int(input("Enter b: "))
c = int(input("Enter c: "))

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

# Eligibility to vote / drive
age = int(input("Enter age: "))
if age >= 18:
    has_id = input("Do you have ID? (y/n): ")
    if has_id == "y":
        print("You can vote ✅")
    else:
        print("Get an ID first 🪪")
else:
    print("Not eligible 🚫")
```
📤 (a=5,b=9,c=7) → `Largest is 9`

---

# 🟣 UNIT 3 — NumPy, Pandas Programs, Matplotlib Basics

---

## 🔹 Q3(A) — Four attributes of a NumPy array (4 marks)

| Attribute | Meaning | Example output |
|-----------|---------|----------------|
| `ndim` 📏 | Number of dimensions | `2` |
| `shape` 📐 | Rows × columns tuple | `(2, 3)` |
| `size` 🔢 | Total elements | `6` |
| `dtype` 🏷️ | Data type of elements | `int64` |
| `itemsize` 💾 | Bytes per element | `8` |
| `nbytes` | Total bytes | `48` |
| `T` 🔄 | Transpose | shape (3,2) |

```python
import numpy as np
a = np.array([[1, 2, 3],
              [4, 5, 6]])
print(a.ndim)       # 2
print(a.shape)      # (2, 3)
print(a.size)       # 6
print(a.dtype)      # int64
print(a.itemsize)   # 8
print(a.T)          # [[1 4] [2 5] [3 6]]
```

## 🔹 Q3(B) — Array creation routines in NumPy, any three (3 marks)

📝 Routines that **create new arrays**. 🔁 See the table in Unit 2 Q2(C) Paper 3. Three examples:
```python
import numpy as np
print(np.zeros((2, 2)))        # [[0. 0.] [0. 0.]]
print(np.ones((2, 3)))         # [[1. 1. 1.] [1. 1. 1.]]
print(np.arange(0, 10, 3))     # [0 3 6 9]
print(np.linspace(0, 1, 3))    # [0.  0.5 1. ]
print(np.eye(2))               # [[1. 0.] [0. 1.]]
```

## 🔹 Q3(B) OR — Short note on conditional selection in NumPy 🔁 → See Unit 2 Q2(B) Paper 3.

---

## 🔹 Q3(C) — Beautiful Soup program to extract all hyperlinks (7 marks)

**Steps:** 1️⃣ Import bs4 2️⃣ Provide HTML (string/file/URL) 3️⃣ Create soup object 4️⃣ `find_all('a', href=True)` 5️⃣ Loop & print `href` and text.

```python
from bs4 import BeautifulSoup

html_doc = """
<html><body>
  <h1>My Links</h1>
  <a href="https://www.google.com">Google</a>
  <a href="https://www.python.org">Python</a>
  <a>No link here</a>
  <a href="/about">About</a>
</body></html>
"""

soup = BeautifulSoup(html_doc, "html.parser")     # parse
links = soup.find_all("a", href=True)             # only <a> having href

for link in links:
    print(link.text, "->", link["href"])
```
📤
```
Google -> https://www.google.com
Python -> https://www.python.org
About -> /about
```
**For a live webpage:**
```python
import requests
soup = BeautifulSoup(requests.get("https://example.com").text, "html.parser")
```

## 🔹 Q3(C) OR — NumPy indexing & slicing problem (7 marks)

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
print(arr[:, -1])
# [20 40 60 80]

# c) Subarray [[30,35],[50,55]]  -> rows 1-2, cols 1-2
print(arr[1:3, 1:3])
# [[30 35]
#  [50 55]]

# d) Replace all elements in 2nd row with 0
arr[1] = 0                # same as arr[1, :] = 0
print(arr)
# [[ 5 10 15 20]
#  [ 0  0  0  0]
#  [45 50 55 60]
#  [65 70 75 80]]
```
🎯 Slicing syntax: `arr[row_start:row_end, col_start:col_end]` (end excluded).

---

## 🔹 Q3(A) (Paper 2) — Multi-Index DataFrame in Pandas (4 marks) 🔁 (also OR in Paper 4)

📝 A **MultiIndex (hierarchical index)** has **two or more index levels** on rows/columns, letting you work with higher-dimensional data in a 2D DataFrame.

```python
import pandas as pd
index = pd.MultiIndex.from_tuples(
    [("India","Delhi"), ("India","Mumbai"), ("USA","NY"), ("USA","LA")],
    names=["Country", "City"])
df = pd.DataFrame({"Population": [32, 21, 8, 4]}, index=index)
print(df)
```
📤
```
                Population
Country City
India   Delhi          32
        Mumbai         21
USA     NY              8
        LA              4
```
*(header shows `Population`)*

**Access:**
```python
print(df.loc["India"])               # outer level
print(df.loc[("USA", "NY")])         # exact
print(df.xs("LA", level="City"))     # cross-section
print(df.groupby(level=0).sum())     # aggregate per country
df2 = df.reset_index()               # back to normal columns
```
Creation also via `pd.MultiIndex.from_product()` or `set_index(["col1","col2"])`.

## 🔹 Q3(B) (Paper 2) — Axes, Ticks and Grid in Matplotlib (3 marks) 🔁 (Q4 B also)

📝
- **Axes** 📐 — the plotting area with X-axis and Y-axis (can have labels, limits).
- **Ticks** 📍 — small marks on axes showing values; controlled by `xticks()`, `yticks()`.
- **Grid** 🔲 — background lines helping read values; `plt.grid()`.

```python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.plot(x, y, marker="o")
plt.xlabel("X-axis")               # axes labels
plt.ylabel("Y-axis")
plt.xlim(0, 6); plt.ylim(0, 12)    # axes limits
plt.xticks([1, 2, 3, 4, 5])        # custom ticks
plt.yticks(range(0, 13, 2), rotation=0)
plt.tick_params(axis="both", direction="in", length=6, colors="red")
plt.grid(True, linestyle="--", color="gray", alpha=0.6)
plt.title("Axes, Ticks & Grid")
plt.show()
```

## 🔹 Q3(B) OR (Paper 2) — Labels, Annotation and Legends in Matplotlib 🔁 (Q4(A) Paper 3 also)

📝
- **Labels** 🏷️ — `xlabel()`, `ylabel()`, `title()` describe axes and chart.
- **Annotation** 💬 — `annotate()` / `text()` adds notes pointing to a data point.
- **Legend** 🗒️ — `legend()` explains what each line/bar represents (needs `label=`).

```python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4]
plt.plot(x, [1, 4, 9, 16], "r-o", label="Square")
plt.plot(x, [1, 8, 27, 64], "b--s", label="Cube")

plt.xlabel("Number"); plt.ylabel("Value"); plt.title("Labels Demo")
plt.annotate("Max point", xy=(4, 64), xytext=(2.5, 50),
             arrowprops=dict(facecolor="black", arrowstyle="->"))
plt.legend(loc="upper left", fontsize=10, title="Series")
plt.show()
```

---

## 🔹 Q3(C) (Paper 2) — NumPy program with 200 random integers (7 marks)

```python
import numpy as np

# 1) 200 random integers from 1 to 200
arr = np.random.randint(1, 201, 200)
print("Array:", arr)

# 2) Standard deviation
print("Standard deviation:", np.std(arr))

# 3) Sum of all elements
print("Sum:", np.sum(arr))

# 4) Elements less than 10
print("Elements < 10:", arr[arr < 10])

# 5) Only odd elements
print("Odd elements:", arr[arr % 2 != 0])

# 6) Reshape to 4 x 50
reshaped = arr.reshape(4, 50)
print("Shape:", reshaped.shape)       # (4, 50)

# 7) Sum of all columns
print("Column sums:", reshaped.sum(axis=0))   # 50 values
```
🎯 `randint(1, 201)` because the high value is **excluded**. `axis=0` → column-wise; `axis=1` → row-wise.

## 🔹 Q3(C) OR (Paper 2) — Restaurant_order.csv (Version A) (7 marks)

```python
import pandas as pd

# 1) Import dataset and assign to rsorder
rsorder = pd.read_csv("http://abc.com/Restaurant_order.csv")
# (if tab separated: sep="\t")

# 2) Names of all columns
print(rsorder.columns)                  # or list(rsorder.columns)

# 3) Number of rows
print(rsorder.shape[0])                 # or len(rsorder)

# 4) Most ordered item
print(rsorder["item_name"].value_counts().idxmax())
# (by quantity ordered:)
print(rsorder.groupby("item_name")["quantity"].sum().idxmax())

# 5) How many of the most ordered item were ordered
top = rsorder.groupby("item_name")["quantity"].sum()
print(top.max())

# 6) Lambda to change type of item_price ("$2.39" -> 2.39)
conv = lambda x: float(x[1:-1]) if isinstance(x, str) else x
rsorder["item_price"] = rsorder["item_price"].apply(conv)
# simpler: rsorder["item_price"].str.replace("$","").astype(float)

# 7) Revenue
revenue = (rsorder["quantity"] * rsorder["item_price"]).sum()
print("Revenue:", revenue)
```
⚠️ Conversion must be done **before** the revenue calculation. In the original chipotle dataset the price looks like `"$2.39 "` (trailing space), hence `x[1:-1]`.

---

## 🔹 Q3(A) (Paper 3) — Time series with example (4 marks)

📝 A **time series** is a sequence of data points **indexed in time order** (daily sales, stock price, temperature). Pandas provides `DatetimeIndex`, `date_range()`, `resample()`, `shift()`, `rolling()`.

```python
import pandas as pd, numpy as np

dates = pd.date_range(start="2024-01-01", periods=6, freq="D")
ts = pd.Series([10, 12, 9, 15, 14, 18], index=dates)
print(ts)
# 2024-01-01    10
# 2024-01-02    12 ...

print(ts["2024-01-03"])                 # 9
print(ts["2024-01-02":"2024-01-04"])    # slicing by date
print(ts.resample("2D").mean())         # downsample
print(ts.rolling(3).mean())             # moving average
print(ts.shift(1))                      # lag
```
Components: **Trend, Seasonality, Cyclic, Noise.** 📈

## 🔹 Q3(B) (Paper 3) — Differentiate Pandas vs NumPy 🔁 → See Unit 2 Q2(A) Paper 2.

## 🔹 Q3(B) OR — Differentiate Join and Merge (3 marks) 🔁 (also Paper 4 Q3(B))

| Feature | `join()` 🔗 | `merge()` 🧬 |
|---------|-----------|--------------|
| Joins on | **Index** (default) | **Columns** (or index with flags) |
| Call style | `df1.join(df2)` method | `pd.merge(df1, df2)` function / `df1.merge(df2)` |
| Default `how` | `left` | `inner` |
| Flexibility | Less | More (`left_on`, `right_on`, `on`) |
| Suffixes | `lsuffix`, `rsuffix` | `suffixes=("_x","_y")` |
| Use when | Index-aligned data | Common key columns |

```python
df1.join(df2, how="inner")
pd.merge(df1, df2, on="id", how="left")
```

---

## 🔹 Q3(C) (Paper 3) — Restaurant_order.csv (Version B) (7 marks)

```python
import pandas as pd

# 1) Import
rsorder = pd.read_csv("http://abc.com/Restaurant_order.csv", sep="\t")

# 2) Number of observations
print(rsorder.shape[0])      # or len(rsorder)

# 3) Most ordered item
item = rsorder.groupby("item_name")["quantity"].sum().idxmax()
print(item)

# 4) How many of that item were ordered
print(rsorder.groupby("item_name")["quantity"].sum().max())

# 5) Most ordered item in choice_description
print(rsorder["choice_description"].value_counts().idxmax())
print(rsorder["choice_description"].value_counts().head(1))

# 6) Total items ordered
print(rsorder["quantity"].sum())

# 7) How many different items are sold
print(rsorder["item_name"].nunique())
```

## 🔹 Q3(C) OR (Paper 3) — Salaries.csv (Version A) (7 marks)

```python
import pandas as pd

# 1) Read as 'sal'
sal = pd.read_csv("Salaries.csv")

# 2) First 25 entries
print(sal.head(25))

# 3) Average BasePay
print(sal["BasePay"].mean())

# 4) Job title of "XYZ"
print(sal[sal["EmployeeName"] == "XYZ"]["JobTitle"])

# 5) Name of highest paid person (TotalPay)
print(sal.loc[sal["TotalPay"].idxmax()]["EmployeeName"])
# or sal[sal["TotalPay"] == sal["TotalPay"].max()]["EmployeeName"]

# 6) Mean BasePay per year (2011-2014)
print(sal.groupby("Year")["BasePay"].mean())

# 7) Job titles represented by only one person in 2013
print((sal[sal["Year"] == 2013]["JobTitle"].value_counts() == 1).sum())
```

---

## 🔹 Q3(A) (Paper 4) — Conditional selection on DataFrame 🔁 → See Unit 1 Q1(C) OR.

## 🔹 Q3(B) (Paper 4) — Differentiate join and merge 🔁 → see above.
## 🔹 Q3(B) OR (Paper 4) — Multi-index DataFrame 🔁 → see Q3(A) Paper 2.

## 🔹 Q3(C) (Paper 4) — Restaurant_order.csv (Version C) (7 marks)

```python
import pandas as pd

# 1) Import
rsorder = pd.read_csv("http://abc.com/restaurant_order.csv", sep="\t")

# 2) First 25 entries
print(rsorder.head(25))

# 3) How is the dataset indexed?
print(rsorder.index)         # RangeIndex(start=0, stop=N, step=1)

# 4) Number of observations
print(rsorder.shape[0])

# 5) Most ordered item
print(rsorder.groupby("item_name")["quantity"].sum().idxmax())

# 6) Most ordered item in choice_description
print(rsorder["choice_description"].value_counts().idxmax())

# 7) Total items ordered
print(rsorder["quantity"].sum())
```
📝 Q3: *"How is the dataset indexed?"* → default **RangeIndex** (0, 1, 2 …).

## 🔹 Q3(C) OR (Paper 4) — Salaries.csv (Version B) (7 marks)

```python
import pandas as pd

sal = pd.read_csv("Salaries.csv")          # 1) read as DataFrame 'sal'
print(sal.tail(25))                         # 2) last 25 entries
print(sal["BasePay"].mean())                # 3) average BasePay
print(sal.columns)                          # 4) names of all columns
print(sal[sal["EmployeeName"] == "XYZ"]["JobTitle"])        # 5) job title of XYZ
print(sal.loc[sal["TotalPay"].idxmax(), "EmployeeName"])    # 6) highest paid
sal.info()                                  # 7) summarize the DataFrame
print(sal.describe())                       #    statistical summary
```
`info()` → dtypes, non-null count, memory; `describe()` → count, mean, std, min, quartiles, max.

---

## 🔹 Q3(A) (Paper 5) — Types of Indexing in NumPy (4 marks)

| Type | Description | Example |
|------|-------------|---------|
| 1️⃣ **Basic (Integer) indexing** | Access single element | `a[0]`, `b[1,2]` |
| 2️⃣ **Negative indexing** | From the end | `a[-1]` |
| 3️⃣ **Slicing** ✂️ | Range `start:stop:step` | `a[1:4]`, `a[::2]` |
| 4️⃣ **Boolean (Conditional) indexing** | Mask | `a[a > 3]` |
| 5️⃣ **Fancy indexing** 🎩 | Array of indices | `a[[0, 2, 4]]` |
| 6️⃣ **Multi-dimensional indexing** | row, col | `b[1:3, 0:2]` |

```python
import numpy as np
a = np.array([10, 20, 30, 40, 50])
print(a[0], a[-1])          # 10 50
print(a[1:4])               # [20 30 40]
print(a[::2])               # [10 30 50]
print(a[a > 25])            # [30 40 50]
print(a[[0, 2, 4]])         # [10 30 50]
b = np.array([[1,2,3],[4,5,6]])
print(b[1, 2])              # 6
print(b[:, 1])              # [2 5]
```

## 🔹 Q3(B) (Paper 5) — Output of the code (3 marks)

```python
import numpy as np
a = np.array([5, 72, 13, 100])
b = np.array([2, 5, 10, 30])
add_ans = a+b
print(add_ans)                 # [  7  77  23 130]
add_ans = np.add(a, b)
print(add_ans)                 # [  7  77  23 130]
c = np.array([1, 2, 3, 4])
add_ans = a+b+c
print(add_ans)                 # [  8  79  26 134]
add_ans = np.add(a, b, c)
print(add_ans)                 # [  7  77  23 130]
```
📤 **Output:**
```
[  7  77  23 130]
[  7  77  23 130]
[  8  79  26 134]
[  7  77  23 130]
```
💡 **Explanation:** `a+b` = `np.add(a,b)` element-wise. `a+b+c` adds all three. In `np.add(a, b, c)` the **third positional argument is `out`**, not a third operand — the result is stored in `c` and returned, so `c` now equals `[7 77 23 130]`. 😮

## 🔹 Q3(B) OR — Any two NumPy arithmetic operators (3 marks)

| Operator | Function | Example |
|----------|----------|---------|
| `+` | `np.add()` | `[1,2]+[3,4] → [4 6]` |
| `-` | `np.subtract()` | `[5,6]-[1,2] → [4 4]` |
| `*` | `np.multiply()` | `[1,2]*[3,4] → [3 8]` |
| `/` | `np.divide()` | `[6,8]/[2,4] → [3. 2.]` |
| `**` | `np.power()` | `[2,3]**2 → [4 9]` |
| `%` | `np.mod()` | `[7,8]%3 → [1 2]` |

```python
a = np.array([10, 20, 30]); b = np.array([1, 2, 3])
print(a + b)     # [11 22 33]
print(a * b)     # [10 40 90]
```
Operations are **element-wise** and use **broadcasting** when shapes differ.

## 🔹 Q3(C) (Paper 5) — List any 5 array creation functions with description (7 marks) 🔁
👉 See the table in **Unit 2 Q2(C) Paper 3** (`array`, `zeros`, `ones`, `full`, `empty`, `eye`, `arange`, `linspace`, `diag`) — each with description and example. Pick any 5.

## 🔹 Q3(C) OR (Paper 5) — Any 5 NumPy data types (7 marks)

| dtype | Description | Size | Example |
|-------|-------------|------|---------|
| `int8/16/32/64` 🔢 | Signed integers | 1/2/4/8 bytes | `np.array([1,2], dtype=np.int32)` |
| `uint8` 🖼️ | Unsigned int (0–255) (images) | 1 byte | `np.uint8(200)` |
| `float32/float64` 🌊 | Decimal numbers | 4/8 bytes | `np.float64(3.14)` |
| `complex64/128` 🧮 | Complex numbers | 8/16 bytes | `1+2j` |
| `bool_` ✅ | True/False | 1 byte | `np.array([True, False])` |
| `str_` / `U` 🔤 | Unicode strings | variable | `np.array(["a","bc"])` |
| `datetime64` 📅 | Dates | 8 bytes | `np.datetime64("2024-01-01")` |
| `object` | Python objects | — | mixed |

```python
import numpy as np
a = np.array([1, 2, 3], dtype=np.float32)
print(a.dtype)                 # float32
b = a.astype(np.int16)         # convert type
print(b.dtype)                 # int16
```

---

# 🟠 UNIT 4 — Missing Data, Scikit-learn, Clustering, EDA, Seaborn, NetworkX

---

## 🔹 Q4(A) — How Pandas handles missing data: `dropna()`, `fillna()`, `interpolate()` (4 marks)

📝 Missing values are shown as **`NaN`** (Not a Number) or `None`. Detect using `isnull()`, `notnull()`, `isna().sum()`.

```python
import pandas as pd, numpy as np
df = pd.DataFrame({"A":[1, np.nan, 3, 4],
                   "B":[5, 6, np.nan, 8]})
print(df.isnull().sum())     # A:1  B:1
```
| Method | Purpose | Example |
|--------|---------|---------|
| `dropna()` 🗑️ | Remove rows/columns with NaN | `df.dropna()` → drops rows 1 and 2 |
| `fillna()` 🩹 | Replace NaN with a value/mean/ffill | `df.fillna(0)` |
| `interpolate()` 📈 | Estimate NaN from neighbouring values | `df.interpolate()` |

```python
print(df.dropna())                    # rows without NaN
print(df.dropna(axis=1))              # drop columns with NaN
print(df.dropna(how="all"))           # drop only if all NaN
print(df.fillna(0))                   # fill with 0
print(df.fillna(df.mean()))           # fill with column mean
print(df.fillna(method="ffill"))      # forward-fill (or df.ffill())
print(df.interpolate())               # linear interpolation
```
📤 `df.interpolate()` → A: `1, 2, 3, 4`; B: `5, 6, 7, 8` ✨

## 🔹 Q4(B) — Setting and resetting index in a DataFrame (3 marks)

📝 **`set_index()`** makes a column the index. **`reset_index()`** moves the index back to a column and restores the default 0,1,2… index.

```python
df = pd.DataFrame({"RollNo":[1,2,3], "Name":["A","B","C"]})

df2 = df.set_index("RollNo")      # RollNo becomes index
print(df2)
#        Name
# RollNo
# 1         A

df3 = df2.reset_index()           # back to default
print(df3)

df2.reset_index(drop=True)        # discard the old index
df.set_index("RollNo", inplace=True)
```
Use: fast lookup by label (`df.loc[2]`), time-series, multi-index.

## 🔹 Q4(B) OR — Time Series in Pandas with simple example 🔁 → See Unit 3 Q3(A) Paper 3.

---

## 🔹 Q4(C) — Employee DataFrame (7 marks)

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

# a) Employees in IT department
print(df[df["Dept"] == "IT"]["Name"])
# 1    Diya
# 2    Karan

# b) Salary greater than 50,000
print(df[df["Salary"] > 50000])
# Diya (55000), Karan (60000), Sahil (70000)

# c) Replace missing Bonus with 0
df["Bonus"] = df["Bonus"].fillna(0)
print(df["Bonus"].tolist())      # [5000.0, 0.0, 8000.0, 0.0, 10000.0]

# d) Average salary per department
print(df.groupby("Dept")["Salary"].mean())
# Dept
# Finance    45000.0
# HR         55000.0
# IT         57500.0
```

## 🔹 Q4(C) OR — Student DataFrame (7 marks)

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
print(df[df["Math"] > 80]["Name"])        # Diya, Karan

# b) Only RollNo and Name columns
print(df[["RollNo", "Name"]])

# c) Add Total column
df["Total"] = df["Math"] + df["Science"]
print(df["Total"].tolist())               # [166, 164, 187, 137, 165]

# d) Average marks in Science
print(df["Science"].mean())               # 83.4
```
(Aarav's Math=78 and Sahil's Math=80 are **not** > 80.)

---

## 🔹 Q4(A) (Paper 2) — Drop columns with at least one missing value (4 marks)

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    "Rollno":     [101, 102, 103],
    "Enrollment": [1111, 1122, 1133],
    "Name":       [np.nan, np.nan, "xyz"]
})
print("Original:\n", df)

result = df.dropna(axis=1, how="any")
print("After dropping columns with NaN:\n", result)
```
📤
```
   Rollno  Enrollment
0     101        1111
1     102        1122
2     103        1133
```
`axis=1` → columns, `how="any"` → drop if **at least one** NaN. The `Name` column is removed.

## 🔹 Q4(B) (Paper 2) — Classes available in Scikit-learn (3 marks)

📝 **Scikit-learn (sklearn)** is the main ML library in Python. Its API is built around **estimator classes** with `fit()`, `predict()`, `transform()`, `score()`.

| Category | Classes / Modules |
|----------|-------------------|
| 🎯 **Classification** | `LogisticRegression`, `KNeighborsClassifier`, `DecisionTreeClassifier`, `RandomForestClassifier`, `SVC`, `GaussianNB` |
| 📈 **Regression** | `LinearRegression`, `Ridge`, `Lasso`, `SVR`, `RandomForestRegressor` |
| 🧩 **Clustering** | `KMeans`, `DBSCAN`, `AgglomerativeClustering` |
| 🗜️ **Dimensionality reduction** | `PCA`, `TruncatedSVD` |
| 🛠️ **Preprocessing** | `StandardScaler`, `MinMaxScaler`, `LabelEncoder`, `OneHotEncoder`, `SimpleImputer` |
| ✂️ **Model selection** | `train_test_split`, `GridSearchCV`, `cross_val_score` |
| 📊 **Metrics** | `accuracy_score`, `confusion_matrix`, `mean_squared_error`, `classification_report` |
| 📝 **Text** | `CountVectorizer`, `TfidfVectorizer` |
| 🔗 **Pipeline** | `Pipeline`, `make_pipeline` |
| 📦 **Datasets** | `load_iris`, `load_digits`, `make_blobs` |

```python
from sklearn.neighbors import KNeighborsClassifier
model = KNeighborsClassifier(n_neighbors=3)
model.fit(X_train, y_train)
pred = model.predict(X_test)
```

## 🔹 Q4(B) OR — Compare Supervised and Unsupervised learning 🔁 → See Unit 5 Q5(A) Paper 3.

---

## 🔹 Q4(C) (Paper 2) — What is clustering? K-Means with 3 clusters on random X, Y (7 marks)

📝 **Clustering** is an **unsupervised learning** technique that **groups similar data points** into clusters without labels (high similarity within a cluster, low between clusters). Applications: customer segmentation, image compression, anomaly detection.

**K-Means algorithm:** 1️⃣ choose K 2️⃣ random initial centroids 3️⃣ assign each point to nearest centroid 4️⃣ recompute centroids = mean of cluster 5️⃣ repeat until stable.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

np.random.seed(42)
X = np.random.rand(100, 1) * 100          # random X values
Y = np.random.rand(100, 1) * 100          # random Y values
data = np.hstack((X, Y))                  # shape (100, 2)

kmeans = KMeans(n_clusters=3, random_state=42, n_init=10)
kmeans.fit(data)

print("Cluster centers:\n", kmeans.cluster_centers_)   # 3 centres
print("Labels:", kmeans.labels_[:10])

plt.scatter(data[:, 0], data[:, 1], c=kmeans.labels_, cmap="viridis")
plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1],
            c="red", marker="X", s=200, label="Centroids")
plt.legend(); plt.title("K-Means (k=3)"); plt.show()
```
📤 e.g. `[[78.1 22.4] [25.3 70.8] [27.9 24.6]]` *(values differ per run without a seed)*.

## 🔹 Q4(C) OR — What is EDA? Explain with Titanic dataset (7 marks)

📝 **Exploratory Data Analysis (EDA)** is the process of **examining a dataset to summarize its main characteristics, find patterns, spot anomalies/outliers, test assumptions** — mostly through statistics and visualization — **before modeling**. 🔍

**Steps:** load → inspect → clean (missing/duplicates) → univariate → bivariate → correlation.

```python
import seaborn as sns, matplotlib.pyplot as plt, pandas as pd
titanic = sns.load_dataset("titanic")

# 1) Inspect
print(titanic.shape)            # (891, 15)
print(titanic.head())
titanic.info()
print(titanic.describe())

# 2) Missing values
print(titanic.isnull().sum())   # age 177, deck 688, embarked 2
titanic["age"] = titanic["age"].fillna(titanic["age"].median())
titanic.drop(columns="deck", inplace=True)

# 3) Univariate
sns.countplot(x="survived", data=titanic); plt.show()
sns.histplot(titanic["age"], kde=True);   plt.show()

# 4) Bivariate
sns.countplot(x="sex", hue="survived", data=titanic); plt.show()
sns.boxplot(x="pclass", y="age", data=titanic);       plt.show()
print(titanic.groupby("sex")["survived"].mean())      # female ~0.74, male ~0.19

# 5) Correlation
sns.heatmap(titanic.corr(numeric_only=True), annot=True, cmap="coolwarm")
plt.show()
```
**Insights:** 👩 females and 🥇 first-class passengers had a higher survival rate; most passengers were 20–40 years old. 🚢

---

## 🔹 Q4(A) (Paper 3) — Label, annotation and legend in Matplotlib 🔁 → See Unit 3 Q3(B) OR (Paper 2).

## 🔹 Q4(B) (Paper 3) — Choropleth graph with an example (3 marks)

📝 A **choropleth map** is a **map in which geographic regions (states, countries) are shaded/colored according to a data value** (population, GDP, COVID cases). Created with **Plotly** (`px.choropleth`) or **GeoPandas/Folium**. 🗺️

```python
import plotly.express as px
import pandas as pd

df = pd.DataFrame({
    "country": ["India", "USA", "Brazil", "Germany", "Australia"],
    "value":   [140, 33, 21, 8, 2.6]
})
fig = px.choropleth(df,
                    locations="country",
                    locationmode="country names",
                    color="value",
                    color_continuous_scale="Viridis",
                    title="Population (in crores/10M) Choropleth")
fig.show()
```
Darker/lighter shades = higher/lower values. Good for geographic comparison; avoid with raw counts when area sizes differ (use density).

## 🔹 Q4(B) OR — NetworkX with an undirected graph (3 marks)

```python
import networkx as nx, matplotlib.pyplot as plt
G = nx.Graph()                                  # undirected
G.add_edges_from([("A","B"), ("B","C"), ("C","A"), ("C","D")])
print(G.nodes(), G.edges())
print("Degree:", dict(G.degree()))              # {'A':2,'B':2,'C':3,'D':1}
nx.draw(G, with_labels=True, node_color="skyblue", node_size=900)
plt.show()
```
Edges have **no direction**: A–B same as B–A. Neighbors: `list(G.neighbors("C"))` → `['B','A','D']`.

---

## 🔹 Q4(C) (Paper 3) — Heatmap on marksheet.csv handling missing data (7 marks)

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Columns: Roll No., Name, DS, PDS, SE, WT, PSC
df = pd.read_csv("marksheet.csv")

# Handle missing data
print(df.isnull().sum())
subjects = ["DS", "PDS", "SE", "WT", "PSC"]
df[subjects] = df[subjects].fillna(df[subjects].mean())   # fill with mean
# or: df = df.dropna()

# Heatmap of subject marks (students as rows)
data = df.set_index("Name")[subjects]
plt.figure(figsize=(8, 6))
sns.heatmap(data, annot=True, cmap="YlGnBu", linewidths=0.5, fmt=".0f")
plt.title("Subject-wise Marks Heatmap 🔥")
plt.xlabel("Subjects"); plt.ylabel("Students")
plt.show()

# (Optional) correlation between subjects
sns.heatmap(data.corr(), annot=True, cmap="coolwarm"); plt.show()
```

## 🔹 Q4(C) OR (Paper 3) & Q4(C) OR (Paper 4) — Countplot and Boxplot with Titanic 🔁 (7 marks)

```python
import seaborn as sns
import matplotlib.pyplot as plt

titanic = sns.load_dataset("titanic")

# Countplot -> number of passengers in each category
plt.figure(figsize=(6, 4))
sns.countplot(x="pclass", hue="survived", data=titanic, palette="Set2")
plt.title("Passengers by Class and Survival")
plt.show()

# Boxplot -> distribution of age per class
plt.figure(figsize=(6, 4))
sns.boxplot(x="pclass", y="age", data=titanic, palette="pastel")
plt.title("Age Distribution by Passenger Class")
plt.show()
```
**Countplot** shows **counts** of each category (bar height = frequency). **Boxplot** shows **min, Q1, median, Q3, max & outliers** (dots beyond whiskers).
```
      ┬  ← max (whisker)
   ┌──┴──┐ ← Q3
   │  ─  │ ← median
   └──┬──┘ ← Q1
      ┴  ← min      ● outliers
```

---

## 🔹 Q4(A) (Paper 4) — Different types of line appearances in Matplotlib (4 marks)

📝 Lines can be customized using **linestyle (`ls`), color (`c`), linewidth (`lw`), marker, alpha**.

| Linestyle | Code | Look |
|-----------|------|------|
| Solid | `'-'` / `'solid'` | ───── |
| Dashed | `'--'` | - - - - |
| Dotted | `':'` | ····· |
| Dash-dot | `'-.'` | -·-·-· |

| Marker | `'o'` circle, `'s'` square, `'^'` triangle, `'*'` star, `'+'`, `'x'`, `'D'` diamond |
|--------|-----|
| Colors | `'r'`, `'g'`, `'b'`, `'k'`, `'#FF5733'`, `'orange'` |

```python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4]
plt.plot(x, [1, 2, 3, 4], "r-",  linewidth=2, label="solid")
plt.plot(x, [2, 3, 4, 5], "g--", linewidth=2, label="dashed")
plt.plot(x, [3, 4, 5, 6], "b:",  marker="o", label="dotted")
plt.plot(x, [4, 5, 6, 7], "m-.", marker="s", markersize=8, label="dash-dot")
plt.legend(); plt.show()
```

## 🔹 Q4(B) (Paper 4) — Axis, Ticks and Grid 🔁 → See Unit 3 Q3(B) Paper 2.

## 🔹 Q4(B) OR (Paper 4) — NetworkX with directed graph (3 marks)

```python
import networkx as nx, matplotlib.pyplot as plt
G = nx.DiGraph()                                   # directed graph
G.add_edges_from([("A","B"), ("B","C"), ("C","A"), ("A","D")])
print("In-degree :", dict(G.in_degree()))          # {'A':1,'B':1,'C':1,'D':1}
print("Out-degree:", dict(G.out_degree()))         # {'A':2,'B':1,'C':1,'D':0}
print("Successors of A:", list(G.successors("A"))) # ['B','D']
nx.draw(G, with_labels=True, arrows=True, node_color="lightgreen",
        node_size=900, arrowsize=20)
plt.show()
```
Edges have **direction** (A→B ≠ B→A). Used for web links, workflows, Twitter follows. 🔗

---

## 🔹 Q4(C) (Paper 4) — LMplot and heatmap with random data (7 marks)

```python
import numpy as np, pandas as pd
import seaborn as sns, matplotlib.pyplot as plt

np.random.seed(0)
df = pd.DataFrame({
    "x": np.random.rand(50) * 10,
})
df["y"] = 2 * df["x"] + np.random.randn(50) * 2     # linear + noise
df["group"] = np.random.choice(["A", "B"], 50)

# LMplot : scatter + regression line
sns.lmplot(x="x", y="y", data=df, hue="group", height=5)
plt.title("LMPlot")
plt.show()

# Heatmap with random data
data = np.random.rand(5, 5)
sns.heatmap(data, annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Heatmap of Random Data 🔥")
plt.show()
```
`lmplot` creates a **FacetGrid**; regression line + 95 % confidence band is drawn automatically.

## 🔹 Q4(C) OR (Paper 4) — Countplot & Boxplot with Titanic 🔁 → see above.

---

## 🔹 Q4(A) (Paper 5) — DataFrame from dictionary of Series (4 marks)

```python
import pandas as pd
people_dict = {
 "weight":    pd.Series([68, 83, 112], index=["alice", "bob", "charles"]),
 "birthyear": pd.Series([1984, 1985, 1992], index=["bob", "alice", "charles"], name="year"),
 "children":  pd.Series([0, 3], index=["charles", "bob"]),
 "hobby":     pd.Series(["Biking", "Dancing"], index=["alice", "bob"]),
}
people = pd.DataFrame(people_dict)
print(people)
```
📤
```
         weight  birthyear  children    hobby
alice        68       1985       NaN   Biking
bob          83       1984       3.0  Dancing
charles     112       1992       0.0      NaN
```
💡 **Explanation:** Pandas **aligns the Series by index labels** (not by position). The row index is the union of all labels (`alice, bob, charles`). `birthyear` values are matched by label (alice=1985, bob=1984). Missing labels → `NaN`; `children` becomes `float` (because of NaN). The `name="year"` of the Series is ignored — the **dictionary key** is used as column name.

## 🔹 Q4(B) (Paper 5) — What is `reset_index()` in Pandas? (3 marks)
## 🔹 Q4(B) OR — Use of `reset_index()` method

📝 `reset_index()` **resets the DataFrame's index to the default integer index (0,1,2,…)**, and by default **moves the old index into a new column**.

**Syntax:** `df.reset_index(level=None, drop=False, inplace=False)`

```python
import pandas as pd
df = pd.DataFrame({"Marks":[80, 90, 70]}, index=["A","B","C"])

print(df.reset_index())
#   index  Marks
# 0     A     80

print(df.reset_index(drop=True))     # discards old index
#    Marks
# 0     80

# Common use: after filtering / sorting
f = df[df["Marks"] > 70]             # index: A, B
f = f.reset_index(drop=True)         # 0, 1
```
**Uses:** clean index after `dropna()`/filter/sort; convert MultiIndex levels back to columns after `groupby()`.

## 🔹 Q4(C) (Paper 5) — Any 5 Pandas Series functions (7 marks)

| Function | Description | Example |
|----------|-------------|---------|
| `head(n)` / `tail(n)` | First/last n elements | `s.head(3)` |
| `sum()`, `mean()`, `max()`, `min()` | Aggregates | `s.mean()` |
| `value_counts()` | Frequency of unique values | `s.value_counts()` |
| `unique()` / `nunique()` | Unique values / count | `s.unique()` |
| `sort_values()` | Sort | `s.sort_values(ascending=False)` |
| `apply(func)` | Apply function to each element | `s.apply(lambda x: x*2)` |
| `isnull()` / `fillna()` / `dropna()` | Missing data | `s.fillna(0)` |
| `describe()` | Summary statistics | `s.describe()` |
| `idxmax()` | Index label of maximum | `s.idxmax()` |
| `cumsum()` | Cumulative sum | `s.cumsum()` |

```python
import pandas as pd
s = pd.Series([10, 20, 20, 40, None], index=list("abcde"))
print(s.sum())                       # 90.0
print(s.mean())                      # 22.5
print(s.value_counts())              # 20 -> 2 ...
print(s.sort_values(ascending=False))
print(s.fillna(0).apply(lambda x: x + 1))
print(s.idxmax())                    # 'd'
```

## 🔹 Q4(C) OR (Paper 5) — Concatenation and Merge with example (7 marks)

### 🔗 `pd.concat()` — stacks DataFrames **along an axis** (rows or columns)
```python
import pandas as pd
df1 = pd.DataFrame({"id":[1,2], "name":["A","B"]})
df2 = pd.DataFrame({"id":[3,4], "name":["C","D"]})

print(pd.concat([df1, df2]))                       # vertical (axis=0)
print(pd.concat([df1, df2], ignore_index=True))    # reset index 0..3
print(pd.concat([df1, df2], axis=1))               # side by side
```
📤 (`ignore_index=True`)
```
   id name
0   1    A
1   2    B
2   3    C
3   4    D
```
### 🧬 `pd.merge()` — joins on **common key columns** (SQL-style)
```python
emp = pd.DataFrame({"id":[1,2,3], "name":["A","B","C"]})
sal = pd.DataFrame({"id":[1,2,4], "salary":[100,200,300]})
print(pd.merge(emp, sal, on="id"))                # inner
print(pd.merge(emp, sal, on="id", how="outer"))
```
| | **concat** | **merge** |
|---|-----------|-----------|
| Combines | Stack/append | Join by keys |
| Needs common column | ❌ | ✅ |
| Analogy | Pile of papers 📚 | SQL JOIN 🔗 |

---

# 🔴 UNIT 5 — Matplotlib Programs, Text Features, Machine Learning

---

## 🔹 Q5(A) — Gridlines and ticks; commands to enable gridlines & customize ticks (4 marks)

📝 **Gridlines** 🔲 are horizontal/vertical lines across the plot that help read values. **Ticks** 📍 are small marks (with labels) on an axis indicating value positions (major & minor ticks).

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.arange(1, 6)
y = x ** 2
plt.plot(x, y, marker="o")

# ---- Gridlines ----
plt.grid(True)                                              # enable
plt.grid(True, which="both", axis="both",
         color="gray", linestyle="--", linewidth=0.5)       # customized
plt.grid(axis="y")                                          # only horizontal

# ---- Ticks ----
plt.xticks([1, 2, 3, 4, 5], ["One","Two","Three","Four","Five"], rotation=30)
plt.yticks(np.arange(0, 30, 5))
plt.tick_params(axis="both", which="major", direction="in",
                length=7, width=2, colors="red", labelsize=10)
plt.minorticks_on()                                         # minor ticks

plt.title("Grid & Ticks"); plt.show()
```
Using OOP: `ax.grid(True)`, `ax.set_xticks([...])`, `ax.tick_params(...)`.

## 🔹 Q5(B) — Boxplot of scores (3 marks)

```python
import matplotlib.pyplot as plt
scores = [55, 67, 89, 45, 78, 90, 100, 60]

plt.boxplot(scores)
plt.ylabel("Marks")
plt.title("Student Scores")
plt.show()
```
📊 Sorted: 45, 55, 60, 67, 78, 89, 90, 100 → **median = (67+78)/2 = 72.5**, Q1 ≈ 57.5, Q3 ≈ 89.5. No outliers.

## 🔹 Q5(B) OR — Histogram with 5 bins (3 marks)

```python
import matplotlib.pyplot as plt
Ages = [18, 22, 25, 19, 30, 27, 24, 21, 20, 23, 26]

plt.hist(Ages, bins=5, color="skyblue", edgecolor="black")
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.title("Age Distribution")
plt.show()
```
Range 18–30 → each bin width = 12/5 = **2.4**; the bars show how many ages fall in each interval.

---

## 🔹 Q5(C) — Line chart of 5 students' marks, two subjects, export to PDF (7 marks)

```python
import matplotlib.pyplot as plt

students = ["S1", "S2", "S3", "S4", "S5"]
math     = [78, 85, 92, 67, 80]
science  = [88, 79, 95, 70, 85]

plt.figure(figsize=(8, 5))
plt.plot(students, math,    color="blue",  linestyle="--", marker="o", label="Math")
plt.plot(students, science, color="green", linestyle="-.", marker="s", label="Science")

plt.xlabel("Students"); plt.ylabel("Marks")
plt.title("Marks of 5 Students")
plt.legend(); plt.grid(True, alpha=0.4)

# Annotation for the highest mark (95, Science of S3)
all_marks = math + science
hi = max(all_marks)                                  # 95
plt.annotate(f"Highest: {hi}", xy=("S3", hi), xytext=("S4", hi + 2),
             arrowprops=dict(facecolor="red", arrowstyle="->"),
             fontsize=11, color="red")
plt.ylim(60, 100)

plt.savefig("marks_chart.pdf", format="pdf", bbox_inches="tight")   # export PDF
plt.show()
```
🎯 `savefig()` **before** `show()` — otherwise a blank file is saved! 🤣

## 🔹 Q5(C) OR — Bar chart of sales of 5 products, value on top, PNG export (7 marks)

```python
import matplotlib.pyplot as plt

products = ["Laptop", "Phone", "Tablet", "Watch", "Camera"]
sales    = [150, 300, 120, 200, 90]
colors   = ["#FF6B6B", "#4ECDC4", "#FFD93D", "#6C5CE7", "#2ECC71"]

plt.figure(figsize=(8, 5))
bars = plt.bar(products, sales, color=colors, edgecolor="black")

for bar in bars:                                   # value on top of each bar
    h = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2, h + 3, str(h),
             ha="center", va="bottom", fontweight="bold")

plt.xlabel("Products"); plt.ylabel("Sales (units)")
plt.title("Sales of 5 Products")
plt.savefig("sales_chart.png", dpi=300, bbox_inches="tight")   # export PNG
plt.show()
```
(Newer Matplotlib: `plt.bar_label(bars)`.)

---

## 🔹 Q5(A) (Paper 2) — TF-IDF with example (4 marks)

📝 **TF-IDF (Term Frequency – Inverse Document Frequency)** is a text-vectorization technique that gives each word a **weight showing its importance in a document relative to a collection (corpus)**. Common words (the, is) get low weight; rare, meaningful words get high weight. ⚖️

**Formulas:**
- **TF(t,d)** = (times term t appears in d) / (total terms in d)
- **IDF(t)** = log( N / df(t) ) (N = number of documents; df = documents containing t) *(sklearn uses smoothed: log((1+N)/(1+df)) + 1)*
- **TF-IDF = TF × IDF**

**Example:** D1 = "I love python", D2 = "I love data science"
- TF("python", D1) = 1/3 ≈ 0.333; IDF = log(2/1) ≈ 0.301 (log₁₀) → TF-IDF ≈ **0.100**
- TF("love", D1) = 1/3; IDF = log(2/2) = 0 → TF-IDF = **0** (common word, no importance).

```python
from sklearn.feature_extraction.text import TfidfVectorizer
docs = ["I love python", "I love data science"]
vec = TfidfVectorizer()
X = vec.fit_transform(docs)
print(vec.get_feature_names_out())   # ['data' 'love' 'python' 'science']
print(X.toarray().round(2))
```

## 🔹 Q5(B) (Paper 2) — Generalization, Overfitting and Underfitting (3 marks)
## 🔹 Q5(B) OR (Paper 3) — same 🔁

| Term | Meaning | Train Error | Test Error | Emoji |
|------|---------|-------------|-----------|-------|
| **Generalization** | Model performs well on **new, unseen data** — the goal of ML | Low | Low | 🎯 |
| **Overfitting** | Model **memorizes training data** incl. noise; poor on new data (high variance) | Very low | High | 🤓 |
| **Underfitting** | Model **too simple**; fails to capture pattern (high bias) | High | High | 😴 |

```
  Underfit          Good fit           Overfit
  ──────────        ∿∿∿∿∿∿             /\/\/\/\/\/ (passes through every point)
  (straight line    (follows trend)    (follows noise)
   for curved data)
```
**Causes/Remedies:**
- Overfitting: complex model, little data → use **more data, regularization (L1/L2), cross-validation, pruning, dropout, simpler model**.
- Underfitting: too simple model, few features → **use complex model, add features, train longer**.

🤣 *Overfitting = student who memorized last year's paper but fails when the questions change. Underfitting = student who didn't study at all.*

## 🔹 Q5(B) OR (Paper 2) — Confusion matrix with example (3 marks) 🔁 (also Paper 4)

📝 A **confusion matrix** is a table that **summarizes the performance of a classification model** by comparing actual vs predicted classes.

|  | **Predicted Positive** | **Predicted Negative** |
|---|---|---|
| **Actual Positive** | ✅ TP (True Positive) | ❌ FN (False Negative) |
| **Actual Negative** | ❌ FP (False Positive) | ✅ TN (True Negative) |

**Metrics:**
- Accuracy = (TP + TN) / Total
- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- F1 = 2·P·R / (P + R)

**Example:** Spam detection, 100 emails → TP=40, FN=10, FP=5, TN=45
- Accuracy = (40+45)/100 = **0.85**; Precision = 40/45 = **0.89**; Recall = 40/50 = **0.80**.

```python
from sklearn.metrics import confusion_matrix, accuracy_score, classification_report
y_true = [1, 0, 1, 1, 0, 1, 0, 0]
y_pred = [1, 0, 1, 0, 0, 1, 1, 0]
print(confusion_matrix(y_true, y_pred))
# [[3 1]
#  [1 3]]
print(accuracy_score(y_true, y_pred))   # 0.75
```

---

## 🔹 Q5(C) (Paper 2) — Linear Regression + program to predict future iPhone price (7 marks)

📝 **Linear Regression** is a **supervised** algorithm that models the relationship between a **dependent variable (y)** and one or more **independent variables (x)** by fitting a straight line: **y = mx + c** (m = slope, c = intercept). It predicts **continuous** values. Best line = minimum **Mean Squared Error** (least squares).

**CSV columns:** `iphoneNumber, model_name, price` (iphoneNumber = generation number such as 6, 7, 8…)

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

# 1) Load data
df = pd.read_csv("iphone.csv")
# iphoneNumber  model_name   price
#      6        iPhone 6     40000 ...

# 2) Features and target
X = df[["iphoneNumber"]]          # 2D
y = df["price"]

# 3) Train
model = LinearRegression()
model.fit(X, y)
print("Slope m    :", model.coef_[0])
print("Intercept c:", model.intercept_)

# 4) Predict future price (e.g. iPhone 15)
future = pd.DataFrame({"iphoneNumber": [15]})
print("Predicted price of iPhone 15:", model.predict(future)[0])

# 5) Visualize
plt.scatter(X, y, color="blue", label="Actual")
plt.plot(X, model.predict(X), color="red", label="Regression line")
plt.xlabel("iPhone Number"); plt.ylabel("Price")
plt.legend(); plt.title("iPhone Price Prediction 📱"); plt.show()
```
Evaluate with `model.score(X, y)` (R²).

## 🔹 Q5(C) OR (Paper 2) — Classification + KNN on iris dataset (7 marks)

📝 **Classification** is a **supervised** technique that **predicts a discrete class label** (spam/not spam, species of flower).
**KNN (K-Nearest Neighbors):** classifies a new point by looking at its **K closest training points** (usually **Euclidean distance**) and picking the **majority class**. It is a lazy learner (no training phase).

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, confusion_matrix

# 1) Load built-in iris dataset
iris = load_iris()
X, y = iris.data, iris.target          # 150 samples, 4 features, 3 classes

# 2) Split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42)

# 3) Train
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)

# 4) Predict & evaluate
y_pred = knn.predict(X_test)
print("Accuracy:", accuracy_score(y_test, y_pred))     # ~1.0 / 0.97
print(confusion_matrix(y_test, y_pred))

# 5) Classify a new flower
sample = [[5.1, 3.5, 1.4, 0.2]]
print("Species:", iris.target_names[knn.predict(sample)[0]])   # setosa 🌸
```

---

## 🔹 Q5(A) (Paper 3) — Hashing trick; explain CountVectorizer with example (4 marks)

📝 **Hashing trick (feature hashing):** a technique to convert text/categorical features into **fixed-size numeric vectors** using a **hash function** that maps each token to an index (column) — **no vocabulary is stored**, so it saves memory and handles huge/unknown vocabularies. Drawback: **hash collisions** (two words, same index) and features aren't interpretable. In sklearn: `HashingVectorizer`.

📝 **CountVectorizer** converts a collection of text documents into a **matrix of token counts** (Bag-of-Words): rows = documents, columns = unique words.

```python
from sklearn.feature_extraction.text import CountVectorizer, HashingVectorizer

docs = ["I love python", "I love data science", "python is fun"]
cv = CountVectorizer()
X = cv.fit_transform(docs)
print(cv.get_feature_names_out())
# ['data' 'fun' 'is' 'love' 'python' 'science']
print(X.toarray())
# [[0 0 0 1 1 0]
#  [1 0 0 1 0 1]
#  [0 1 1 0 1 0]]
```
(Default token pattern ignores single-character words like "I".)

```python
hv = HashingVectorizer(n_features=8)          # fixed 8 columns
print(hv.transform(docs).toarray().shape)     # (3, 8)
```

## 🔹 Q5(B) (Paper 3) — Explain Bag of Words model (3 marks) 🔁 (also Q5(B) OR Paper 4)

📝 **Bag of Words (BoW)** represents a text document as an **unordered collection (bag) of its words**, **ignoring grammar and word order but keeping frequency**. Each document becomes a **vector of word counts** over the vocabulary.

**Steps:** 1️⃣ Tokenize 2️⃣ Build vocabulary 3️⃣ Count occurrences per document.

**Example:** D1 = "the cat sat", D2 = "the cat saw the dog"
Vocabulary: `[the, cat, sat, saw, dog]`
| | the | cat | sat | saw | dog |
|--|----|-----|-----|-----|-----|
| D1 | 1 | 1 | 1 | 0 | 0 |
| D2 | 2 | 1 | 0 | 1 | 1 |

```python
from sklearn.feature_extraction.text import CountVectorizer
cv = CountVectorizer()
X = cv.fit_transform(["the cat sat", "the cat saw the dog"])
print(cv.get_feature_names_out())   # ['cat' 'dog' 'sat' 'saw' 'the']
print(X.toarray())                  # [[1 0 1 0 1] [1 1 0 1 2]]
```
**Pros:** simple, effective. **Cons:** loses order/context, sparse, large vocabulary.

## 🔹 Q5(B) OR (Paper 3) — Generalization, overfitting, underfitting 🔁 → see Paper 2 above.

## 🔹 Q5(C) (Paper 3) — What is regression? Explain Linear Regression with example (7 marks)

📝 **Regression** is a supervised ML technique to **predict a continuous numerical value** (price, temperature, salary) from input features. Types: **Linear, Multiple, Polynomial, Ridge/Lasso, Logistic (actually classification)**.

**Linear regression:** `y = β₀ + β₁x` (simple); `y = β₀ + β₁x₁ + β₂x₂ + …` (multiple). Parameters estimated by **least squares**, minimizing `Σ(y − ŷ)²`.

**Metrics:** MSE, RMSE, MAE, **R²** (closer to 1 = better).

**Example:** Predict salary from years of experience.
```python
import numpy as np
from sklearn.linear_model import LinearRegression

X = np.array([[1], [2], [3], [4], [5]])           # experience
y = np.array([30000, 35000, 40000, 45000, 50000]) # salary

model = LinearRegression().fit(X, y)
print("Slope:", model.coef_[0])          # 5000.0
print("Intercept:", model.intercept_)    # 25000.0
print("Predict 6 yrs:", model.predict([[6]])[0])   # 55000.0
print("R2:", model.score(X, y))          # 1.0
```
Equation → **salary = 25000 + 5000 × experience**.

## 🔹 Q5(C) OR (Paper 3) — What is classification? Explain k-Nearest Neighbours with example 🔁 → see Q5(C) OR Paper 2 (theory + iris example). Quick steps:
1️⃣ Choose K 2️⃣ Compute distance (Euclidean: √Σ(xᵢ−yᵢ)²) to all training points 3️⃣ Pick K nearest 4️⃣ Majority vote → class.
Small K → overfitting (noisy); large K → underfitting (smooth). **Scale features** before KNN!

**Mini example:** training points A(1,1)=Red, B(2,2)=Red, C(6,6)=Blue, D(7,7)=Blue. New point (2,1), K=3 → nearest: A, B, then C or D → majority **Red** 🔴.

---

## 🔹 Q5(A) (Paper 4) — Differentiate Supervised and Unsupervised Learning (4 marks) 🔁

| Feature | **Supervised** 👨‍🏫 | **Unsupervised** 🕵️ |
|---------|-------------------|---------------------|
| Data | **Labeled** (input + output) | **Unlabeled** (input only) |
| Goal | Predict outcome / label | Discover hidden patterns/structure |
| Feedback | Yes (teacher/true labels) | No |
| Types | Classification, Regression | Clustering, Association, Dimensionality reduction |
| Algorithms | Linear/Logistic Regression, KNN, SVM, Decision Tree | K-Means, DBSCAN, PCA, Apriori |
| Complexity | Simpler to evaluate (accuracy) | Harder to evaluate |
| Example | Spam detection, house-price prediction | Customer segmentation |

## 🔹 Q5(B) (Paper 4) — Explain confusion matrix with an example 🔁 → See Paper 2 Q5(B) OR above.
## 🔹 Q5(B) OR (Paper 4) — Bag of words 🔁 → see above.

## 🔹 Q5(C) (Paper 4) — What is regression? Explain Logistic Regression with example (7 marks)

📝 **Regression** → see above. **Logistic Regression** is a **supervised classification algorithm** (despite the name) that predicts the **probability** that an input belongs to a class (binary: 0/1, Yes/No). It applies the **sigmoid function** to a linear equation:

**σ(z) = 1 / (1 + e⁻ᶻ)**, where z = β₀ + β₁x₁ + …
Output between 0 and 1; if **p ≥ 0.5 → class 1**, else class 0.

```
 p
1 │            ______ 
  │          /
0.5│-------/-----   (S-shaped sigmoid curve)
  │  ____/
0 └──────────────── z
```
**Example:** Predict whether a student passes based on study hours.
```python
import numpy as np
from sklearn.linear_model import LogisticRegression

hours  = np.array([[1], [2], [3], [4], [5], [6], [7], [8]])
passed = np.array([0, 0, 0, 0, 1, 1, 1, 1])

model = LogisticRegression()
model.fit(hours, passed)
print(model.predict([[2.5], [6.5]]))         # [0 1]
print(model.predict_proba([[4.5]]))          # [[0.5 0.5]] approx
print(model.score(hours, passed))            # 1.0
```
**Types:** binary, multinomial (softmax), ordinal.

## 🔹 Q5(C) OR (Paper 4) — What is clustering? Explain K-Means with an example (7 marks) 🔁
👉 Theory and algorithm in **Unit 4 Q4(C) Paper 2**. Short worked example:

Points: (1,2), (1,4), (1,0), (10,2), (10,4), (10,0); K=2.
```python
from sklearn.cluster import KMeans
import numpy as np
X = np.array([[1,2],[1,4],[1,0],[10,2],[10,4],[10,0]])
km = KMeans(n_clusters=2, random_state=0, n_init=10).fit(X)
print(km.labels_)            # [1 1 1 0 0 0]
print(km.cluster_centers_)   # [[10. 2.] [ 1. 2.]]
print(km.predict([[0, 0], [12, 3]]))    # [1 0]
```
Choose K with the **Elbow method** (plot `km.inertia_` vs K) 💪.

---

## 🔹 Q5(A) (Paper 5) — Draw the graph for the following code (4 marks)

```python
x = np.array([1, 2, 3, 4])
y = x*2                 # y = [2, 4, 6, 8]
plt.plot(x, y); labels "X-axis", "Y-axis", title "Any suitable title"
```
**Points plotted:** (1,2), (2,4), (3,6), (4,8) → a **straight, upward-sloping line (slope = 2)** passing through these points.
```
Y-axis
 8 |                 ●
 6 |           ●
 4 |      ●
 2 | ●
   +----+----+----+----→ X-axis
     1    2    3    4
        Any suitable title
```
✅ Line with positive slope; x-axis range 1–4, y-axis range 2–8; title "Any suitable title" at the top (e.g., "Linear Graph y = 2x").

## 🔹 Q5(B) (Paper 5) — Draw the graph for the following code (3 marks)

```python
x = [10,20,30,40,50]
y = [30,30,30,30,30]
plt.plot(x, y)
```
Points: (10,30), (20,30) … (50,30) → a **horizontal straight line at y = 30** (slope 0).
```
Y
40 |
30 |●─────●─────●─────●─────●
20 |
   +---10---20---30---40---50--→ X
```

## 🔹 Q5(B) OR (Paper 5) — Draw the graph with two lines (3 marks)

```python
plt.plot(x, y, label="line 1")   # (10,30)…(50,30): horizontal line y = 30
plt.plot(y, x, label="line 2")   # (30,10),(30,20),(30,30),(30,40),(30,50): vertical line x = 30
plt.legend()
```
Line 1 → **horizontal** at y = 30 (x from 10 to 50). Line 2 → **vertical** at x = 30 (y from 10 to 50). They **intersect at (30, 30)** ➕. The legend shows `line 1` (blue) and `line 2` (orange).
```
Y
50 |         |
40 |         |
30 |──●──●───┼───●──●──   ← line 1
20 |         |
10 |         |            ← line 2 (vertical at x=30)
   +--10--20--30--40--50→ X
```

## 🔹 Q5(C) (Paper 5) — Draw a line from (1,3) to (2,8), then (6,1), and finally (8,10) (7 marks)

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 2, 6, 8])
ypoints = np.array([3, 8, 1, 10])

plt.plot(xpoints, ypoints, color="purple", marker="o", linewidth=2)
plt.xlabel("X-axis"); plt.ylabel("Y-axis")
plt.title("Line through given positions")
plt.grid(True)
plt.show()
```
**Shape:** zig-zag — rises steeply (1,3)→(2,8), falls sharply to (6,1), then climbs to (8,10) ("N/W"-like pattern).
```
10 |                          ●(8,10)
 8 |    ●(2,8)                /
 3 |●(1,3)                   /
 1 |          \      ●(6,1) /
   +--1--2--3--4--5--6--7--8--→
```

## 🔹 Q5(C) OR (Paper 5) — Types of Charts in Matplotlib (7 marks)

| # | Chart | Function | Use | Example |
|---|-------|----------|-----|---------|
| 1 | 📈 **Line** | `plt.plot()` | Trends over time | `plt.plot(x, y)` |
| 2 | 📊 **Bar / Barh** | `plt.bar()`, `plt.barh()` | Compare categories | `plt.bar(names, vals)` |
| 3 | 🧱 **Histogram** | `plt.hist()` | Frequency distribution | `plt.hist(data, bins=5)` |
| 4 | ⚪ **Scatter** | `plt.scatter()` | Relationship between 2 variables | `plt.scatter(x, y)` |
| 5 | 🥧 **Pie** | `plt.pie()` | Proportions of a whole | `plt.pie(vals, labels=l, autopct="%1.1f%%")` |
| 6 | 📦 **Box** | `plt.boxplot()` | Spread, median, outliers | `plt.boxplot(data)` |
| 7 | 🌊 **Area** | `plt.fill_between()` / `stackplot()` | Cumulative magnitude | `plt.fill_between(x, y)` |
| 8 | 🎻 **Violin** | `plt.violinplot()` | Density + box | |
| 9 | 🔥 **Heatmap / imshow** | `plt.imshow()` | Matrix values | |
| 10 | 🧩 **Subplots** | `plt.subplots()` | Multiple charts | |

```python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(2, 3, figsize=(12, 7))
ax[0,0].plot([1,2,3],[2,4,6]);        ax[0,0].set_title("Line")
ax[0,1].bar(["A","B","C"],[5,8,3]);   ax[0,1].set_title("Bar")
ax[0,2].hist([1,2,2,3,3,3,4],bins=4); ax[0,2].set_title("Histogram")
ax[1,0].scatter([1,2,3],[3,1,4]);     ax[1,0].set_title("Scatter")
ax[1,1].pie([40,30,30], labels=["X","Y","Z"], autopct="%1.0f%%"); ax[1,1].set_title("Pie")
ax[1,2].boxplot([2,4,5,7,9]);         ax[1,2].set_title("Box")
plt.tight_layout(); plt.show()
```

---
---

# 🏁 Final Exam Tips 🎯

| ✅ Do | ❌ Don't |
|------|---------|
| Start with a **definition** | Jump directly into code |
| Add **syntax + example + output** | Write code without output |
| Draw **diagrams / tables** | Write long paragraphs only |
| Use **import statements** | Forget `import numpy as np` |
| Write **comments** in code | Leave code unexplained |
| Mention **real-life use** | Ignore applications |

**Marks strategy:** 3-marks → definition + 1 example • 4-marks → definition + points + example • 7-marks → definition + diagram + 5–6 points + full code + output.

🤣 *"If your code works on the first try, check if you're dreaming."* 💤
🎉 **ALL THE BEST FOR YOUR EXAM! 🍀📚🚀** 🎉
