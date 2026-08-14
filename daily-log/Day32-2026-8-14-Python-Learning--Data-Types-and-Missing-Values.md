# Day 32-2026-8-14-Python-Learning --Data Types and Missing Values

## 今天学到的

1. `.dtype` 查看一列的数据类型，`df.dtypes` 查看整表每列的类型。
2. `.astype()` 转换一列的类型（比如整数转浮点数、转字符串）。
3. 索引本身也有类型，可以用 `.index.dtype` 查看。
4. 缺失值用 `.isnull()` 找，`df[df["列"].isnull()]` 能筛出缺失所在的行。
5. `.fillna(x)` 填补缺失值；`.replace(旧值, 新值)` 替换某个非缺失的值。
6. 缺失值用 0 填补会拉低平均值——填之前要想清楚"缺失"到底该算什么。

---

## 示例

数据：某班级同学参加社团评分，两人成绩暂缺（还没打分）。

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    "name":  ["李明","王芳","张伟","赵敏","陈静"],
    "club":  ["篮球社","篮球社","合唱团","合唱团","合唱团"],
    "score": [85, 92, np.nan, 78, np.nan],
})
```

**1. 查看类型**
```python
print(df["score"].dtype)   # float64（有缺失值时整数列会自动变浮点）
```

**2. astype 转换类型**
```python
print(df["name"].astype(str).dtype)   # object / str
```

**3. 找出缺失值**
```python
print(df[df["score"].isnull()])
#   name club  score
# 2  张伟  合唱团    NaN
# 4  陈静  合唱团    NaN

print(df["score"].isnull().sum())   # 2
```

**4. fillna 填补缺失**
```python
avg = df["score"].mean()            # 85.0，计算均值时自动跳过 NaN
print(df["score"].fillna(avg).tolist())
# [85.0, 92.0, 85.0, 78.0, 85.0]
```

**5. replace 替换某个值**
```python
club = pd.Series(["篮球社","合唱团","篮球社"])
print(club.replace("篮球社", "球类社").tolist())
# ['球类社', '合唱团', '球类社']
```

---

## 我犯的错

**把缺失分数直接填成 0，导致平均分被拉低**

```python
print(df["score"].fillna(0).mean())
# 51.0
```
我一开始觉得"没打分就当 0 分"很合理，直接 `fillna(0)`，结果班级平均分从 85 分掉到了 51 分。

原因：这两位同学是"还没评分"，不是"考了 0 分"，缺失和 0 含义完全不同。用 0 填补相当于把"未知"当成了"最差"，平均分被严重低估。

修正：改用已有分数的均值（或干脆先 `dropna()` 只算已打分的人）：
```python
print(df["score"].fillna(df["score"].mean()).mean())
# 85.0
```

---

## 还没搞懂的问题

1. `.fillna()` 除了填一个固定值，能不能给不同的列填不同的值？
2. 如果一整行好几列都缺失，`isnull()` 怎么一次判断"这一行是不是缺了很多东西"？

---

