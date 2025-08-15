# 📊 Pandas Cheat Sheet

Pandas is a Python library for data manipulation and analysis.
This guide covers **Series** and **DataFrame** with essential methods, attributes, and examples.

---

## **1. Import Pandas**

```python
import pandas as pd
```

---

## **2. Pandas Series**

A **Series** is a one-dimensional labeled array.

```python
# Creating a Series
s = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'])
```

| Method / Attribute | Description                 | Example                  |
| ------------------ | --------------------------- | ------------------------ |
| `s.values`         | Numpy array of values       | `s.values`               |
| `s.index`          | Index (labels)              | `s.index`                |
| `s.dtype`          | Data type                   | `s.dtype`                |
| `s.head(n)`        | First `n` elements          | `s.head(2)`              |
| `s.tail(n)`        | Last `n` elements           | `s.tail(2)`              |
| `s.sum()`          | Sum of values               | `s.sum()`                |
| `s.mean()`         | Mean of values              | `s.mean()`               |
| `s.unique()`       | Unique values               | `s.unique()`             |
| `s.nunique()`      | Count unique values         | `s.nunique()`            |
| `s.value_counts()` | Frequency count             | `s.value_counts()`       |
| `s.apply(func)`    | Apply function element-wise | `s.apply(lambda x: x*2)` |

---

## **3. Pandas DataFrame**

A **DataFrame** is a two-dimensional labeled data structure.

```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['NY', 'LA', 'SF']
}
df = pd.DataFrame(data)
```

---

### **Basic Info & Structure**

| Method / Attribute | Description                   | Example         |
| ------------------ | ----------------------------- | --------------- |
| `df.shape`         | Dimensions (rows, cols)       | `df.shape`      |
| `df.info()`        | Column info & data types      | `df.info()`     |
| `df.describe()`    | Statistical summary (numeric) | `df.describe()` |
| `df.head(n)`       | First `n` rows                | `df.head(5)`    |
| `df.tail(n)`       | Last `n` rows                 | `df.tail(5)`    |
| `df.columns`       | Column names                  | `df.columns`    |
| `df.index`         | Row index                     | `df.index`      |
| `df.dtypes`        | Column data types             | `df.dtypes`     |

---

### **Selection & Indexing**

| Method                   | Description                   | Example                     |
| ------------------------ | ----------------------------- | --------------------------- |
| `df['col']`              | Select a column               | `df['Name']`                |
| `df[['col1','col2']]`    | Select multiple columns       | `df[['Name','City']]`       |
| `df.loc[labels, labels]` | Label-based selection         | `df.loc[0:2, 'Name':'Age']` |
| `df.iloc[rows, cols]`    | Position-based selection      | `df.iloc[0:2, 0:2]`         |
| `df.at[label, label]`    | Single value (label-based)    | `df.at[0, 'Name']`          |
| `df.iat[row, col]`       | Single value (position-based) | `df.iat[0, 0]`              |

---

### **Filtering**

| Example                                       | Description                |
| --------------------------------------------- | -------------------------- |
| `df[df['Age'] > 30]`                          | Filter rows where Age > 30 |
| `df[(df['Age'] > 25) & (df['City'] == 'NY')]` | Multiple conditions        |
| `df[df['Name'].isin(['Alice', 'Bob'])]`       | Filter by values           |
| `df[df['City'].str.startswith('N')]`          | String condition           |

---

### **Modifying**

| Method                     | Description      | Example                               |
| -------------------------- | ---------------- | ------------------------------------- |
| `df['New'] = values`       | Add column       | `df['Country'] = 'USA'`               |
| `df.rename(columns={...})` | Rename columns   | `df.rename(columns={'Age':'Years'})`  |
| `df.drop(columns=[...])`   | Drop columns     | `df.drop(columns=['City'])`           |
| `df.drop(index=[...])`     | Drop rows        | `df.drop(index=[0,2])`                |
| `df.replace({...})`        | Replace values   | `df.replace({'NY':'New York'})`       |
| `df.astype(type)`          | Change data type | `df['Age'] = df['Age'].astype(float)` |

---

### **Missing Data**

| Method              | Description         | Example             |
| ------------------- | ------------------- | ------------------- |
| `df.isnull()`       | Detect NaNs         | `df.isnull()`       |
| `df.isnull().sum()` | Count NaNs          | `df.isnull().sum()` |
| `df.dropna()`       | Drop rows with NaNs | `df.dropna()`       |
| `df.fillna(value)`  | Fill NaNs           | `df.fillna(0)`      |

---

### **Statistics & Aggregation**

| Method                     | Description           | Example                          |
| -------------------------- | --------------------- | -------------------------------- |
| `df.sum()`                 | Column-wise sum       | `df.sum()`                       |
| `df.mean()`                | Column-wise mean      | `df.mean()`                      |
| `df.min()`                 | Column-wise min       | `df.min()`                       |
| `df.max()`                 | Column-wise max       | `df.max()`                       |
| `df.std()`                 | Standard deviation    | `df.std()`                       |
| `df['col'].value_counts()` | Frequency count       | `df['City'].value_counts()`      |
| `df.corr()`                | Correlation matrix    | `df.corr()`                      |
| `df.agg({...})`            | Multiple aggregations | `df.agg({'Age':['mean','max']})` |

---

### **Sorting**

| Method                                                        | Description       | Example                             |
| ------------------------------------------------------------- | ----------------- | ----------------------------------- |
| `df.sort_values(by='col')`                                    | Sort by column    | `df.sort_values(by='Age')`          |
| `df.sort_values(by=['col1','col2'], ascending=[True, False])` | Multi-column sort | `df.sort_values(by=['City','Age'])` |
| `df.sort_index()`                                             | Sort by index     | `df.sort_index()`                   |

---

### **GroupBy**

| Method                             | Description           | Example                                          |
| ---------------------------------- | --------------------- | ------------------------------------------------ |
| `df.groupby('col')`                | Group by column       | `df.groupby('City')`                             |
| `df.groupby('col')['col2'].mean()` | Group & aggregate     | `df.groupby('City')['Age'].mean()`               |
| `df.groupby('col').agg({...})`     | Multiple aggregations | `df.groupby('City').agg({'Age':['mean','max']})` |

---

### **Exporting**

| Method                                  | Description     | Example            |
| --------------------------------------- | --------------- | ------------------ |
| `df.to_csv('file.csv', index=False)`    | Export to CSV   | Save without index |
| `df.to_excel('file.xlsx', index=False)` | Export to Excel | Save without index |
| `df.to_json('file.json')`               | Export to JSON  | Save as JSON       |

