# Day 14-2026-7-26-Python-Learning



## 1.今天学了什么

* 嗯之前提到过的布尔值booleans，相比起直接在代码里输入“True”和“False”，使用比较符号来决定输出正确与否更能运用到不同场景（可以参考day10的表格）。
* 同样大小的浮点数和整数比较时是相等的，输出“True”；但若将数值用“”引起来，不相等输出“False”。
* 再次强调，“==”才是比较是否相等，“=”是赋值。
* ### 布尔值组合：and / or / not

  * 用来拼接多个条件，得到最终 True / False
  * 三个逻辑运算符

    1. and（并且），两边条件全部为True，结果才是True；只要一个False → False。**A and B**
    2. or（或者），两边任意一个为True，结果就是True；全部False才是False。**A or B**
    3. not（取反），反转真假：not True = False 、not False = True
  * **运算优先级** ：and 优先级高于 or
eg. True or True and False
执行顺序：先算 True and False → 得到 False
再算 True or False → 最终 True

    * 最好多用括号，不要死记，括号能明确优先级顺序，避免bug。
* ### Conditionals（条件语句）

  * 末尾加“：”，满足条件的代码块必须缩进，“elif" ="else if”，可以写多个，“else”可选，放在最后。
  * 只有缩进内的代码才属于当前if分支。



* ### Boolean conversion（布尔转换）

  * Python 会自动把数据分为「真值(truthy)」和「假值(falsey)」，bool() 函数可以把任意值转为布尔类型
  * 真值（转为True）：非0数字、非空字符串、非空列表
  * 假值（转为False）：0、空字符串""、空列表\[]、None
  * if 判断里，不需要强制写bool()，Python自动隐式转换，即if 后面不一定非要写 == True / == False
直接放数字、字符串都行，Python会自动调用bool()转换。

    * if 0:
print(0)
elif "spam":
print("spam")
spam





## 2.有什么问题

* ！！我刚刚知道为什么之前的表格都打不出来了，，，，需要在表格前一行回车，保证和前一行之间有空行。
* 感觉这节课学得有点emmm懵懵的确实难起来了。。。好吧还能理解，而且用英语看得也比较熟练了。
* 又有点想学英语了，，

