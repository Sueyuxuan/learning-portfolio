# Day 24-2026-8-6-Python-Learning  索引与数据筛选--Pandas



## 1\. 基础取列（Native accessors）

\- 共有两种拿到列数据的写法，结果一样
		- 方式1：点语法，简洁，列名不能带空格/特殊字符
			reviews.country
		- 方式2：方括号，通用，列名有符号也能用，优先推荐这个
			reviews\['country']
		再取某一行的单个值：
			reviews\['country']\[0]





## 2\. pandas两套索引：iloc 和 loc

\- \*\*iloc\*\*：按数字位置取（0开始，左闭右开，和普通python切片一样）
		- 语法：df.iloc\[行,列]，先行后列，和普通python反过来


|代码|说明|
|-|-|
|`reviews.iloc\[0]`|取第0整行|
|`reviews.iloc\[:, 0]`|全部行，第0列|
|`reviews.iloc\[1:3, 0]`|1、2行，第0列（切片不包含3）|
|`reviews.iloc\[\[0,1,2],0]`|指定多行：0,1,2行，取第0列|
|`reviews.iloc\[-5:]`|取倒数5行|

\- \*\*loc\*\*：按标签名字取（索引名、列名字）

	 - df.loc\[行标签, 列标签]

	- 注意：loc切片左右都包含！和iloc不一样！
		reviews.loc\[0, 'country']   //index=0这一行，country列
		reviews.loc\[:, \['taster\_name','points']]  //全部行，指定多列

	区分：
 	- iloc：看位置序号，0:10取0‑9，不包含末尾
	- loc：看标签名字，0:10会把0到10全部取出来，包含10
		- 如果index刚好是0,1,2,3数字，容易踩坑！


## 3\. 修改索引 set\_index()

\- DataFrame的index不是固定不变，可以换成别的列当做索引
		reviews.set\_index("title")
	//原来的行号会被替换成title那一列的值。适合有意义标识的字段。


## 4\. 条件筛选（conditional selection）

\- 先产出一堆True/False布尔Series，再丢进loc里面过滤数据。

		- 单条件
		产出布尔序列
			reviews.country == 'Italy'
		把True对应的行筛选出来
			reviews.loc\[reviews.country == 'Italy']

		- 多条件
		\& = and 同时满足，每个条件必须加括号
		| = or 满足其中一个

	- pandas内置筛选函数

		1. .isin() 判断是否在列表里面
		2. .notnull() / .isnull() 判断空值NaN


## 5\. 给数据赋值 Assigning data

\- 新建/改写一列

	- 全部行填同一个常量
		reviews\['critic'] = 'everyone'

	- 用可迭代对象批量赋值
		reviews\['index\_backwards'] = range(len(reviews), 0, -1)


注意，就像刚才提到的，loc和iloc切片范围不一样，数字索引下最容易翻车。同时，loc多条件\&、|，每个条件一定要套括号，不然报错



虽然pandas的内容还有部分没有学完，但我大概已经掌握一些完成基本代码梳理的能力，明天开始要注重个人项目的完成了。
同时要尽快提高完成任务的效率，争取高效高质地结束。

