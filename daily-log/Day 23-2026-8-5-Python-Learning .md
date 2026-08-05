# Day 23-2026-8-5-Python-Learning  有关建表格--Pandas

**Creating,Reading and Writing**
	- 这一节就是教怎么搞出来表格，以及怎么把外面的表格文件读进代码里

## DataFrame（完整的一张表，相当于Excel的sheet）
	- 用pd.DataFrame()来创建

- 往里丢字典：字典的key就是列名字，value是这一列所有的数据，写成列表
	pd.DataFrame({'Yes': [50, 21], 'No': [131, 2]})
	//运行完就出来一张表，左边自动生成0、1这种数字，这是行号。

- 表格里面不光能放数字，字符串文字也完全可以
	pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'],
              'Sue': ['Pretty good.', 'Bland.']})

- but如果不想用0、1当行标签，那就用index=自己起名
	pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'],
         		'Sue': ['Pretty good.', 'Bland.']},
          	   index=['Product A', 'Product B'])
	//index只是给每行起个标识，不会改动原本的数据。
	
## Series（就单独的一列）
	-  DataFrame是整张表，Series就是拆出来单独的一列，一维的，不是完整表格

- 可以简单拿个列表直接生成
	pd.Series([1, 2, 3, 4, 5])
- Series也可以自定义index，还有自己的name（这一列的名字）
	pd.Series([30, 35, 40],
          	index=['2015 Sales', '2016 Sales', '2017 Sales'],
          	name='Product A')
	//DataFrame说白了就是一堆Series拼到一起凑出来的大表格。


## 读取本地CSV文件
	- 平时干活几乎不会手写造表格，大多是读取已经存在的数据文件

- csv就是很常见的表格文件，用逗号隔开各个格子内容

- pd.read_csv(文件路径)，直接把csv读成DataFrame
	wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv")
	//两个很常用查看数据的小工具

1. .shape
看这个表格多大，返回(行数,列数)
比如(129971, 14)，代表129971行，14列
wine_reviews.shape
2. .head()
直接打印前5行，快速瞟一眼数据长啥样，不用加载全部
wine_reviews.head()

学完这节课干后，
学会手动建表、分清DataFrame和Series，学会读取csv文件。

但注意，
还没做筛选、计算这些分析操作，只是把数据弄到代码里面。



其实刚开始还没明白这节课的内容价值所在，但现在看来，这节课是pandas的入门基础，核心就是搞懂__DataFrame__整张表格和__Series__单列这两个核心对象。
学会读取csv把外部数据导入代码，并用shape、head快速摸清数据集基本情况。
本身不做数据分析，但所有后续筛选、统计都建立在这一步之上，相当于__把原材料准备好__。