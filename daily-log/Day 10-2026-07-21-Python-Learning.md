# Day 10-2026-07-21-Python-Learning



## 1.今天学了什么

* Conditions and condition statement(条件和条件语句)
* 这个主要是为了应对不同条件而做出·不同反应，可以理解为数学中的分段函数。比如，x<3, y=x+; x>=3,y=5x.

  * ### Conditions（条件）

    * 是要么为正确要么错误的情况。在Python中有很多写条件的不同方式，但最常见的是比较两个不同的值。

  \- #直接输出比较的内容即可
print(2>3)
False

  * 也可以将变量赋值后比较变量，变量和数值。
  * 一些比较常见的符号和意义：
| Symbols | Meanings                  |
| ------- | ------------------------- |
| ==      | equals                    |
| !=      | does not equal            |
| <       | less than                 |
| <=      | less than or equal to     |
| >       | greater than              |
| >=      | greater than or equal to  |
  * 需要特别注意的是，“=”是赋值而不是等于，“==”才是等于。
  * ### Conditional Statements（条件语句）

    * 使用条件来修改函数运行的方式。它们检查条件的值，如果条件评估为True，则执行特定的代码块（ 否则，如果条件为 False，则不会运行代码。）。
    * 最常见的**if**语句。

      def evaluate\_temp(temp):
#Set an initial message
message = "Normal temperature."
#Update value of message only if temperature greater than 38
if temp > 38:
message = "Fever!"
return message

    * 注意到此处有两级indentation缩进：

      * def：后，所属此函数的代码必须缩进。
      * if：后，只有满足条件才运行的代码，需要再缩进一层（也就是fever那一层）。

    \-后续会学到配套语句逻辑：

*  if ：第一个判断条件
*  elif ：前面if不成立，再做第二个判断
*  else ：前面所有if/elif都不成立，兜底执行

  * 这三类语句下方的执行代码，全都需要额外一层缩进，规则和本次if完全一致。
  * **if...else**语句。
  * if后的语句运行为True，else后的运行为False。

    * def evaluate\_temp\_with\_else(temp):
if temp > 38:
message = "Fever!"   //缩进一层
else:
message = "Normal temperature."  //缩进一层
return message
  * **if...elif...else**语句。
  * （即“else if”的缩写）来检查多个条件是否可能为真。

    \-def evaluate\_temp\_with\_elif(temp):
if temp > 38:
message = "Fever!"
elif temp > 35:
message = "Normal temperature."
else:
message = "Low temperature."
return message

## 2.一些碎碎念

* 今天改了一些之前日志里的格式错误，比如某级标题“#”后需空格，无需标题的“-”“\*”也需要空格。
* 然后在写这篇的时候突然发现，技术部左上方的“查看”可以预览md格式的已编排格式，方便我将编辑页面和最终格式进行比对。
* 但·我还是不知道表格为什么打不出来，没找到问题在哪，，，，嗯等我再研究研究。

