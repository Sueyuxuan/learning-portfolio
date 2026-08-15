# Day 33-2026-8-15-Python-Learning --Renaming and Combining

## 今天学到的

1. `.rename(columns={...})` 改列名。
2. `.rename_axis()` 改索引/列这个"轴"本身的名字（不是改某一列的名字，是给索引起名）。
3. `pd.concat([a, b])` 把两张**列相同**的表上下拼起来。
4. `.join()` 把两张**索引相同**的表左右拼起来（按索引对齐，不是按某一列）。
5. 两张表 `.join()` 时如果有同名列，必须用 `lsuffix`/`rsuffix` 区分，否则报错。

---

## 示例代码

**1. rename 改列名**
```python
import pandas as pd

df = pd.DataFrame({"name": ["李明","王芳","张伟"], "score": [85, 92, 78]})
r = df.rename(columns={"name": "student_name"})
print(list(r.columns))
# ['student_name', 'score']
```

**2. rename_axis 给索引起名**
```python
r2 = df.rename_axis("row_id", axis="rows")
print(r2.index.name)
# row_id
```

**3. concat：拼两个社团的名单**
```python
basketball_fall = pd.DataFrame({"name": ["李明"], "score": [85]})
basketball_spring = pd.DataFrame({"name": ["王芳"], "score": [92]})

all_members = pd.concat([basketball_fall, basketball_spring], ignore_index=True)
print(all_members)
#   name  score
# 0  李明     85
# 1  王芳     92
```

**4. join：按姓名把成绩表和出勤表拼起来**
```python
scores = pd.DataFrame({"score": [85, 92]}, index=["李明", "王芳"])
attendance = pd.DataFrame({"days": [20, 18]}, index=["李明", "王芳"])

combined = scores.join(attendance)
print(combined)
#     score  days
# 李明     85    20
# 王芳     92    18
```

---

## 我犯的错

**错误 1：join 时两张表有同名列，直接报错**

```python
midterm = pd.DataFrame({"count": [1, 2]}, index=["A班", "B班"])
final   = pd.DataFrame({"count": [3, 4]}, index=["A班", "B班"])
midterm.join(final)
```
报错：
```
ValueError: columns overlap but no suffix specified: Index(['count'], dtype='str')
```
原因：两张表都有 `count` 列，`join` 不知道该保留哪个、怎么区分。

修正：加上 `lsuffix`/`rsuffix` 区分来源：
```python
print(midterm.join(final, lsuffix="_期中", rsuffix="_期末"))
#     count_期中  count_期末
# A班         1         3
# B班         2         4
```

**错误 2：concat 两张表列名没对齐，以为会自动合并成一列**

```python
a = pd.DataFrame({"name": ["李明"], "score": [85]})
b = pd.DataFrame({"name": ["王芳"], "点数": [92]})
print(pd.concat([a, b], ignore_index=True))
#   name  score    点数
# 0   李明   85.0   NaN
# 1   王芳    NaN  92.0
```
我以为 `score` 和 `点数` 都是"分数"，会自动对齐到一列，结果 `concat` 只认**列名**，名字不一样就各自变成一列，缺的地方补 `NaN`。

修正：拼接前先统一列名：
```python
b = b.rename(columns={"点数": "score"})
print(pd.concat([a, b], ignore_index=True))
#   name  score
# 0   李明     85
# 1   王芳     92
```

---

## 还没搞懂的问题

1. `join` 和 `concat` 到底该怎么选？如果两张表既不是同索引也不是同列名，该用哪个？
2. `rename_axis` 起的这个"轴的名字"平时有什么实际用处？

---


