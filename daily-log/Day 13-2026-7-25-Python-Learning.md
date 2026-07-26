# Day 13-2026-7-25-Python-Learning


## 1.今天学了什么

- ### Help
	- Python内置查询工具， 查看任意函数/类型的官方使用说明，无需上网查。
	- 注意，查函数时只写函数名称，如help（round），不能写整个函数，比如help（round（2.5））。否则，按照运算顺序，先运行round（2.5）算出结果，再执行help（结果），最后查的不是函数说明而是数字说明。
	- help显示的内容：函数参数格式，函数功能的英文说明，以及参数可选/必填规则。

- ### Defining functions
	- def函数名（参数）：
		  函数代码               //缩进
		  return 返回值          //向外输出结果，结束函数

- ### Docstring（文档字符串）
	- 给自己写的函数加说明，让help（）能显示解释。
	- 函数头下第一行，三引号包裹，可换行，可写示例
	- def least_difference(a, b, c):
    """Return the smallest difference between any two numbers
    among a, b and c.
    
    >>> least_difference(1, 5, -5)
    4
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
	- 输入help（函数名）会显示我写的功能解释+示例
	- 注意，为规范习惯，正式代码所有自定义函数都要写docstring

- ### Functions that don't return
	- 函数没有return，默认返回None（空值），即使内部有计算，不写return外部就拿不到结果。
	- print和help无需return，只做事不返回数据。

- ### Default argument（默认参数 ）
	- 给参数设置默认值，调用函数时可以不传这个参数。
	- 比较经典的一些默认参数：“sep=' ' ”, 多个值之间的分隔符，默认空格；"end='\n' "，结尾默认换行。

- ### Functions Applied to Functions（高阶函数）
	- 可以接受另一个函数作为参数的函数（类似嵌套函数？）
	- def mod_5(x):
    """Return the remainder of x after dividing by 5"""
    return x % 5

print(
    'Which number is biggest?',
    max(100, 51, 14),
    'Which number is the biggest modulo 5?',
    max(100, 51, 14, key=mod_5),
    sep='\n',
)
Which number is biggest?
100
Which number is the biggest modulo 5?
14


## 2.有什么问题
- 我感觉有点难了诶，，，特别是各种函数放在一起太容易晕了。
- 除了学习知识点还需要自己多写写代码，相信熟能生巧吧。
