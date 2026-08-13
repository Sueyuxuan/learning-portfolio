# Day 31-2026-8-13-Python-Learning --Grouping and Sorting

## 今天学到的

1. `groupby()` 不止能求和/计数，配合 `apply()` 能对每组做任意自定义处理。
2. `groupby(...).apply(lambda ...)` 可以从每组里取出满足某条件的**整行**，而不只是一个数。
3. 按多个列分组会得到 `MultiIndex`（多层索引），用 `.reset_index()` 拍平回普通表。
4. `.agg([...])` 可以一次算多个统计量，里面可以直接传函数本身（如 `len, min, max`），不用写字符串。
5. `sort_index()` 按索引（分组名）排序，`sort_values()` 按数值排序——两者不是一回事。
6. `sort_values()` 默认是**升序**。

---

## 示例

数据：某年级三个班的一次测验成绩。

```python
import pandas as pd

df = pd.DataFrame({
    "class":   ["1班","1班","2班","2班","2班","3班"],
    "student": ["李明","王芳","李明","张伟","张伟","王芳"],
    "score":   [85, 92, 78, 95, 88, 90],
})
```

**1. groupby + count 对比 value_counts**
```python
print(df.groupby("class")["class"].count().to_dict())
# {'1班': 2, '2班': 3, '3班': 1}
print(df["class"].value_counts().to_dict())
# {'2班': 3, '1班': 2, '3班': 1}
```
结果一样，只是排序方式不同：`groupby+count` 按分组名排，`value_counts` 按次数排。

**2. apply(lambda)：取每个班分数最高的那一行**
```python
top = df.groupby("class").apply(lambda d: d.loc[d.score.idxmax()])
print(top)
#       student  score
# class
# 1班        王芳     92
# 2班        张伟     95
# 3班        王芳     90
```
`.max()` 只能给出最高分是多少，`apply` 能连带告诉我是谁考的。

**3. 多列分组 → MultiIndex → reset_index**
```python
mi = df.groupby(["class","student"]).score.agg([len])
print(mi)
#                len
# class student
# 1班    李明        1
#       王芳        1
# 2班    张伟        2
#       李明        1
# 3班    王芳        1

print(mi.reset_index())
#   class student  len
# 0    1班      李明    1
# 1    1班      王芳    1
# 2    2班      张伟    2
# 3    2班      李明    1
# 4    3班      王芳    1
```

**4. agg 一次算多个统计量**
```python
print(df.groupby("class").score.agg([len, min, max]))
#        len  min  max
# class
# 1班       2   85   92
# 2班       3   78   95
# 3班       1   90   90
```

**5. sort_index vs sort_values**
```python
avg = df.groupby("class").score.mean()
print(avg.sort_index())
# 1班    88.5
# 2班    87.0
# 3班    90.0

print(avg.sort_values(ascending=False))
# 3班    90.0
# 1班    88.5
# 2班    87.0
```

---

## 我犯的错

**错误 1：把 `sort_index()` 当成按分数排序**

写了 `avg.sort_index()`，以为会把平均分最高的班排在最前面，结果发现顺序还是按班级名（1班→2班→3班），根本没按分数排。

原因：`sort_index()` 排的是索引（班级名），不是数值。要按分数排必须用 `sort_values()`。

**错误 2：`sort_values()` 没加 `ascending=False`**

写了 `avg.sort_values()`，结果平均分最高的 3 班排在了最后一行。

原因：`sort_values()` 默认升序（从小到大）。要从高到低必须加 `ascending=False`。

---

## 还没搞懂的问题

1. `apply(lambda ...)` 能不能一次返回好几个新字段，而不只是一整行？
2. `agg([len, min, max])` 里的 `len` 和 `.count()` 在有缺失值时结果会不会不一样？

---

