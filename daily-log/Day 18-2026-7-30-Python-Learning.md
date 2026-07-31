# Day 18-2026-7-30-Python-Learning   循环与列表推导式（Loops & List Comprehensions）


## 学习课程
Kaggle Python · Lesson 5: Loops and List Comprehensions

## 今日学习目标
搞懂 for / while 两种循环的区别，会用 range() 生成数字序列，能看懂并写出基础的列表推导式。

## ① 概念用自己的话说

循环解决的核心问题是：**当我要对一堆数据做同样一件事时，不用把代码复制粘贴很多遍，让程序自己一个一个处理。**

### for 循环
用来**遍历可迭代对象**（列表、元组、字符串等），自动依次取出里面的每一个元素。

基本结构：

```python
for 变量 in 可迭代对象:
    执行语句
```

示例：

```python
planets = ['Mercury', 'Venus', 'Earth']
for planet in planets:
    print(planet)
```

运行时，`planet` 会依次变成 `'Mercury'`、`'Venus'`、`'Earth'`，每次都执行一遍 `print`。

### range()
用来**生成一串数字序列**，规则是**左闭右开**（包含起点，不包含终点）。

```python
range(5)   # 代表 0, 1, 2, 3, 4，不包含 5
```

常和 for 搭配，用来"重复固定次数"：

```python
for i in range(5):
    print(i)          # 依次输出 0 1 2 3 4
```

### while 循环
**只要条件为真，就一直循环**；条件变为假时退出。

```python
i = 0
while i < 10:
    print(i)
    i += 1            # 关键：必须更新变量，否则条件永远成立 → 死循环
```

- 条件为 `True` → 继续执行循环体
- 条件为 `False` → 退出循环

> ⚠️ `i += 1` 必须写在循环体**内部**（缩进对齐）。如果漏掉或缩进错位，`i` 永远是 0，`i < 10` 永远成立，程序会卡死。

**for 和 while 怎么选**：知道要循环多少次（或有现成的列表/序列）用 for；不确定次数、靠某个条件决定何时停用 while。

### 列表推导式 List Comprehension（Python 特色）
把"循环 + 生成新列表"压缩成一行，是 Python 很有代表性的写法。

**基础格式**：`[表达式 for 变量 in 对象]`

```python
squares = [n**2 for n in range(10)]
# 得到 [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

**带筛选条件**：`[表达式 for 变量 in 对象 if 条件]`

```python
short_planets = [planet for planet in planets if len(planet) < 6]
# 只保留名字长度小于 6 的行星
```

**转换 + 筛选同时进行**：

```python
[planet.upper() + '!' for planet in planets if len(planet) < 6]
# 先筛选出短名字，再转成大写并加感叹号
```

等价的普通循环写法（帮助理解推导式其实是"循环的缩写"）：

```python
result = []
for planet in planets:
    if len(planet) < 6:
        result.append(planet.upper() + '!')
```

### 小技巧 Tips
- **布尔值可参与运算**：`True` 当作 1，`False` 当作 0。
- 利用这条规则可以快速**统计列表里满足条件的元素个数**，例如统计负数数量：

```python
sum(num < 0 for num in nums)
# num < 0 对每个元素返回 True/False，求和即为负数个数
```

- 原则：**可读性优于简洁**。推导式虽短，但如果逻辑太复杂、一行看不懂，宁可写成普通 for 循环。

## ②还没懂的问题
1. 之前学 C++ 时对循环就不太熟练，虽然 Python 的写法更简单，但在理解和记忆上我还是有点吃力——尤其是列表推导式的"表达式在前、循环在后"这个顺序，和普通 for 循环读起来是反的，容易绕晕。
2. 列表推导式里能不能写 `if...else`？（比如"负数变 0、正数保留"这种既筛选又替换的需求）
3. 到了第三周学 Pandas，是不是就基本不用自己写 for 循环了？循环和后面数据分析的关系是什么？

## 今日小结
有了之前 C++ 的铺垫，学起来比第一次接触循环乐观一些，至少不是完全陌生。for 和 range 比较好懂，列表推导式还需要多写几遍才能形成肌肉记忆。希望后面实践的时候能更顺利一点。

## 明天要复习的问题
列表推导式的三种写法（基础 / 带筛选 / 转换+筛选），明天开始学习前先默写一遍，检验是不是真记住了。
# Day 11：循环与列表推导式（Loops & List Comprehensions）

## 学习日期
2026-07-XX

## 学习课程
Kaggle Python · Lesson 5: Loops and List Comprehensions

## 今日学习目标
搞懂 for / while 两种循环的区别，会用 range() 生成数字序列，能看懂并写出基础的列表推导式。

## ① 概念用自己的话说

循环解决的核心问题是：**当我要对一堆数据做同样一件事时，不用把代码复制粘贴很多遍，让程序自己一个一个处理。**

### for 循环
用来**遍历可迭代对象**（列表、元组、字符串等），自动依次取出里面的每一个元素。

基本结构：

```python
for 变量 in 可迭代对象:
    执行语句
```

示例：

```python
planets = ['Mercury', 'Venus', 'Earth']
for planet in planets:
    print(planet)
```

运行时，`planet` 会依次变成 `'Mercury'`、`'Venus'`、`'Earth'`，每次都执行一遍 `print`。

### range()
用来**生成一串数字序列**，规则是**左闭右开**（包含起点，不包含终点）。

```python
range(5)   # 代表 0, 1, 2, 3, 4，不包含 5
```

常和 for 搭配，用来"重复固定次数"：

```python
for i in range(5):
    print(i)          # 依次输出 0 1 2 3 4
```

### while 循环
**只要条件为真，就一直循环**；条件变为假时退出。

```python
i = 0
while i < 10:
    print(i)
    i += 1            # 关键：必须更新变量，否则条件永远成立 → 死循环
```

- 条件为 `True` → 继续执行循环体
- 条件为 `False` → 退出循环

> ⚠️ `i += 1` 必须写在循环体**内部**（缩进对齐）。如果漏掉或缩进错位，`i` 永远是 0，`i < 10` 永远成立，程序会卡死。

**for 和 while 怎么选**：知道要循环多少次（或有现成的列表/序列）用 for；不确定次数、靠某个条件决定何时停用 while。

### 列表推导式 List Comprehension（Python 特色）
把"循环 + 生成新列表"压缩成一行，是 Python 很有代表性的写法。

**基础格式**：`[表达式 for 变量 in 对象]`

```python
squares = [n**2 for n in range(10)]
# 得到 [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

**带筛选条件**：`[表达式 for 变量 in 对象 if 条件]`

```python
short_planets = [planet for planet in planets if len(planet) < 6]
# 只保留名字长度小于 6 的行星
```

**转换 + 筛选同时进行**：

```python
[planet.upper() + '!' for planet in planets if len(planet) < 6]
# 先筛选出短名字，再转成大写并加感叹号
```

等价的普通循环写法（帮助理解推导式其实是"循环的缩写"）：

```python
result = []
for planet in planets:
    if len(planet) < 6:
        result.append(planet.upper() + '!')
```

### 小技巧 Tips
- **布尔值可参与运算**：`True` 当作 1，`False` 当作 0。
- 利用这条规则可以快速**统计列表里满足条件的元素个数**，例如统计负数数量：

```python
sum(num < 0 for num in nums)
# num < 0 对每个元素返回 True/False，求和即为负数个数
```

- 原则：**可读性优于简洁**。推导式虽短，但如果逻辑太复杂、一行看不懂，宁可写成普通 for 循环。

## ②还没懂的问题
1. 之前学 C++ 时对循环就不太熟练，虽然 Python 的写法更简单，但在理解和记忆上我还是有点吃力——尤其是列表推导式的"表达式在前、循环在后"这个顺序，和普通 for 循环读起来是反的，容易绕晕。
2. 列表推导式里能不能写 `if...else`？（比如"负数变 0、正数保留"这种既筛选又替换的需求）
3. 到了第三周学 Pandas，是不是就基本不用自己写 for 循环了？循环和后面数据分析的关系是什么？

## 今日小结
有了之前 C++ 的铺垫，学起来比第一次接触循环乐观一些，至少不是完全陌生。for 和 range 比较好懂，列表推导式还需要多写几遍才能形成肌肉记忆。希望后面实践的时候能更顺利一点。

## 明天要复习的问题
列表推导式的三种写法（基础 / 带筛选 / 转换+筛选），明天开始学习前先默写一遍，检验是不是真记住了。
