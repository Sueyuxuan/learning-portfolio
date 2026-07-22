# Day 11-2026-07-22-Python-Learning



## 1.今天学了什么

* Lists. 做数据科学时，需要一种组织数据的方法，以便高效地处理数据。Python提供了许多数据结构来存储数据，例如lists列表、sets集合、dictionaries字典和tuples元组。
* 相较于单个列举，更好的做法是将相同的数据表示为 Python 列表。要创建一个列表，需要使用方括号（\[，]）并用逗号分隔每个项目。列表中的每个项目都是Python字符串，因此每个项目都被引号括起来。字符串类型为“list”。
* 刚开始可能看不出来列表和单个列举的区别，但后续有很多复杂任务会变得更容易，比如获取指定位置（第一、第二、第三等）的项，检查项目数量，并添加和删除项目。
* ### Lists

  * Lenth，我们可以用"len()"来输出该列表中数据的数量
  * Index索引，可以根据列表中项目的位置（第一、第二、第三等）来引用列表中的任何项目。

    * 需要注意的是，Python使用**零基索引**，这意味着要获取列表中的第一个条目，需使用0，要获取列表中的第二个条目，需使用 1，，，以此类推，要获取列表中的最后一个条目，需使用列表长度减1。
    * print("First entry:", flowers\_list\[0])
print("Second entry:", flowers\_list\[1])

\#The list has length ten, so we refer to final entry with 9
print("Last entry:", flowers\_list\[9])
First entry: pink primrose
Second entry: hard-leaved pocket orchid
Last entry: globe thistle
- 以上代码中用到的是单个“print”，当单个输出中输出多个量时，用“，”隔开。

\- Slicing切片，还可以提取列表的一部分（例如，前三个条目或最后两个条目）。要提取前 x 个条目，需使用 \[:x]；要拉出最后一个 y 条目，需使用 \[-y:]。

	- 删除，用“.remove（）”。

	- 添加，用“.append（）”。

	- 列表不仅仅用于字符串，可以包含任何数据类型的项，包括布尔值，整数和浮点数。整数和浮点数还有其他的发挥空间，比如寻找最值“min（）”“max（）”，求和“sum（）”，平均值sum（切片）/切片中的数据量
		- 切片规则除上述外，\[a:b]，左闭右开, 包含a不包含b。





## 2\. 有啥想说的

* 嗯目前学完了into programming部分，感觉知识点确实可以掌握，但距离熟练运用并找出错误还有很长的路需要走，慢慢来吧把每一步走踏实了，就像我的一个朋友告诉我的，如果想走高一点哪怕久一点也没关系。

