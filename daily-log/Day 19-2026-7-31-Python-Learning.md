# Day 19-2026-7-31-Python-Learning   字符串与字典（Strings & Dictionaries）


## 今日学习目标
掌握字符串的常用操作和格式化输出，理解字典这种"用名字取值"的数据结构，并会遍历字典。

## ① 概念用自己的话说

今天学的两样东西解决的问题不一样：**字符串**帮我处理"文字"，**字典**帮我用"名字"而不是"编号"去存取数据。

---

### 一、字符串 String

#### 定义与引号
单引号 `' '` 和双引号 `" "` 功能完全一致：

```python
x = 'Pluto is a planet'
y = "Pluto is a planet"
```

**引号嵌套技巧**（当文字本身包含引号时）：

```python
"Pluto's a planet!"      # 双引号包住内容，里面就能直接用单引号
'My dog is named "Pluto"'  # 单引号包住内容，里面就能直接用双引号
```

**转义字符**（用反斜杠让特殊符号"照字面"出现）：

| 写法 | 含义 |
| --- | --- |
| `\'` | 单引号 |
| `\"` | 双引号 |
| `\\` | 反斜杠 |
| `\n` | 换行符 |

**三引号** `"""..."""` / `'''...'''`：支持直接换行书写多行字符串。

#### 字符串支持索引、切片、长度、遍历
语法和列表几乎一样（可以理解成"字符串就是一串字符组成的列表"）：

```python
planet = 'Pluto'
planet[0]      # 'P'    取第 0 位字符（索引从 0 开始）
planet[-3:]    # 'uto'  切片，取最后三位
len(planet)    # 5      获取字符长度
```

#### 字符串不可变（immutable）
不能通过索引修改某个字符，也没有 `.append()`；强行修改会触发 `TypeError`：

```python
planet[0] = 'B'   # ❌ TypeError: 'str' object does not support item assignment
```

想"改"字符串，只能生成一个新的（比如用切片拼接），而不是在原地改。

#### 常用内置方法

```python
claim = "Pluto is a planet!"
claim.upper()         # 全部大写
claim.lower()         # 全部小写
claim.index('plan')   # 查找子串首次出现的位置（返回索引）
claim.startswith("Pluto")  # 判断是否以 Pluto 开头 → True
claim.endswith("planet")   # 判断是否以 planet 结尾 → False（结尾其实是 "planet!"）
```

#### 字符串 ↔ 列表 互相转换
- `.split(分隔符)`：字符串 → 列表，不写分隔符时默认按空格切割
- `"连接符".join(列表)`：列表 → 字符串

```python
"a,b,c".split(",")        # → ['a', 'b', 'c']
"-".join(['2026', '07', '17'])  # → '2026-07-17'
```

#### 字符串格式化 .format()
用 `{}` 作为占位符，会自动转换数据类型，不用手动 `str()`：

```python
planet = "Pluto"
position = 9
text = "{}, you'll always be the {}th planet to me.".format(planet, position)
```

进阶格式控制：

| 写法 | 作用 | 例子 |
| --- | --- | --- |
| `{:.2}` | 保留 2 位有效数字 | 3.14159 → 3.1 |
| `{:.3%}` | 转为百分比（3 位小数） | 0.25 → 25.000% |
| `{:,}` | 数字加千位分隔符 | 1000000 → 1,000,000 |

---

### 二、字典 Dictionary

字典存放**键值对（key: value）**，通过 key 查询对应的 value。和列表的区别是：**列表按位置（编号）找东西，字典按名字找东西**——像通讯录 vs 一排编号储物柜。

```python
numbers = {'one': 1, 'two': 2, 'three': 3}
numbers['one']    # 1，根据 key 取 value
```

#### 新增 & 修改

```python
numbers['eleven'] = 11    # key 不存在 → 新增键值对
numbers['one'] = 'Pluto'  # key 已存在 → 修改对应的值
```

#### 字典推导式（快速批量构建）

```python
planets = ['Mercury', 'Venus', 'Earth']
planet_to_initial = {planet: planet[0] for planet in planets}
# → {'Mercury': 'M', 'Venus': 'V', 'Earth': 'E'}
```

#### in：判断某内容是否为字典的 key

```python
'Saturn' in planet_to_initial   # False（Saturn 不在里面）
```

#### 遍历字典
直接循环字典，默认遍历的是**所有 key**：

```python
for k in numbers:
    print(k, numbers[k])
```

三个常用方法：
- `.keys()`：获取全部键
- `.values()`：获取全部值
- `.items()`：同时拿到 key 和 value（**最常用**）

```python
for planet, initial in planet_to_initial.items():
    print(planet, initial)
```

## ②  还没懂的问题
1. 字符串是"不可变"的，那为什么 `claim.upper()` 又能返回大写版本？是新生成了一个字符串，原来的没变吗？这两件事怎么统一理解？
2. 字典的 key 有没有限制？数字、字符串都能当 key，那列表能不能当 key？
3. 一个字典是怎么变成一张表格的？是不是 key 变列名、value 变一列数据？

## 今日小结
今天信息量比前几天大，字符串方法和格式化占位符（`{:.2}` `{:.3%}` `{:,}`）种类多，光看一遍记不住，得靠后面写例子时反复查、反复用。

**反思**：我注意到一个规律——字符串的索引、切片、遍历，和之前学列表的写法几乎一模一样。一开始我把它们当成两个独立的知识点死记，后来发现只要理解"它们都是一串按顺序排列的东西"，很多操作就能触类旁通，记忆负担一下小了很多。这让我意识到，学 Python 不能一个个孤立地背语法，而要去找不同知识点之间的**共同规律**。字典和列表看起来很像但取值方式不同（一个按名字、一个按编号），这个对比也帮我更清楚各自适合什么场景。相比刚学循环时的吃力，今天我更主动地去"建立联系"了，这种学习状态感觉更对。

## 明天要复习的问题
`.items()` 遍历字典的写法（`for k, v in d.items():`），明天开始前先默写一遍——这是后面处理数据最常用的一个，一定要记牢。

