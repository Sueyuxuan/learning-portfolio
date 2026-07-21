# Day 9 - 2026-07-20 - Python Learning

## 1. 今天学了什么——Data Types

- **Integers（整数）**
  - 包括正整数、负整数和 0，代码中用 `int` 表示。

```python
x = 14
print(x)
print(type(x))

14
<class 'int'>
```

> 以下数据类型都是这个流程，不再赘述。

- **Floats（浮点数，也就是小数）**
  - 可以在 decimal（小数点）后有好多位数，用 `float` 表示。
  - 我们也可以用 fraction（分数）来表示一个浮点数。
  - 处理小数时，一个特别有用的函数是 `round()`，它可以让一个数字四舍五入到指定小数位数。

```python
# Round to 5 decimal places
rounded_pi = round(almost_pi, 5)
print(rounded_pi)
print(type(rounded_pi))

3.14286
<class 'float'>
```

  - 无论何时写一个带有小数点的数字，Python 都会将其识别为浮点数据类型。例如，`1.`（或 `1.0`、`1.00` 等）都会被识别为浮点数，即使这些数字在技术上没有小数部分也是这样。

```python
y_float = 1.
print(y_float)
print(type(y_float))

1.0
<class 'float'>
```

- **Booleans（布尔值）**
  - 表示“真”或“假”，输出值为 `True` 或 `False`。
  - 布尔值用于表示表达式的真值。比如，由于 `1 < 2` 是一个真语句，`z_three` 的值为 `True`。
  - 同时，也可以用 `not` 切换布尔值，例如 `not True` 就等于 `False`。

- **Strings（字符串）**
  - 是包含在**引号**中的字符（如 alphabet letters 字母、punctuation 标点符号、numerical digits 数字或 symbols 符号）的集合。
  - 字符串通常用于表示文本，用 `str` 表示。
  - 可以使用 `len()` 函数获取字符串的长度。例如 `"Hello, Python!"` 的长度为 14，因为它有 14 个字符，包括 space（空格）、comma（逗号）和 exclamation mark（感叹号）。注意，计算长度时不包括引号。
  - 空字符串是一种特殊类型，长度为 0。
  - 在引号里输入数字，依旧是字符串类型。
  - 如果有一个可以转换为浮点数的字符串，我们可以使用 `float()`。但并不总是这样，比如不能将 `"Hello, Python"` 转为浮点数。

```python
my_number = "1.12321"
print(my_number)
print(type(my_number))

also_my_number = float(my_number)
print(also_my_number)
print(type(also_my_number))

1.12321
<class 'float'>
```

  - 就像可以将两个数相加一样，两个字符串也可以相加。它通过连接两个原始字符串来产生一个更长的字符串。

```python
new_string = "abc" + "def"
print(new_string)
print(type(new_string))

abcdef
<class 'str'>
```

  - 需要注意的是，无法用两个字符串进行减法或除法运算，也不能将两个字符串相乘；但可以将一个字符串与一个整数相乘。这会产生一个新的字符串，即原始字符串重复指定次数。
  - 但是不可以将字符串与浮点数相乘，只能与整数相乘。

## 2. 有啥补充的

- 其实我感觉还好，虽然内容多了点，但感觉不算难，偏理论的东西多一点，需要花时间记一记。
- 哦然后就是，我突然发现我把文件另存为的时候可以直接选择 `.md` 格式，而不用选择“所有类型”再改后缀了。。好吧我也不知道为什么突然可以了，我不记得我改动啥了。
- ！！我刚刚明白了，因为需要我在新建记事簿的时候就选择“新建 md 格式”。。。！！！