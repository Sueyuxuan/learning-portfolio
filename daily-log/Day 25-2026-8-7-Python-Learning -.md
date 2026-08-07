# Day 25-2026-8-7-Python-Learning  --Summary Functions and Maps-Pandas



**数据集：wine reviews葡萄酒评分数据**



## 一、汇总统计函数（Summary functions）

\- 用来快速拿到列的统计信息，会自动识别数据类型，数字列输出数值统计，字符串列输出文本统计。



|代码|作用|
|-|-|
|reviews.points.describe()|整列的汇总统计。数值列输出count/mean/std/min/四分位数/max；字符串列输出count/unique/top/freq|
|reviews.points.mean()|求该列平均值|
|reviews.points.unique()|取出这一列所有不重复的值，返回数组|
|reviews.taster\_name.value\_counts()|统计每个唯一值分别出现多少次（统计各个品酒师的评测条数）|

\- describe()很智能：数字列输出统计指标；文本列统计有多少条、多少种不同内容、出现最多的内容以及它的频次。





## 二、Maps 映射转换

\- 把现有数据做变换，生成新数据，不会改动原始表格，返回新对象。

&#x09;### 1. .map()
			-只作用于Series（单列），对每一个元素逐个处理。
				review\\\_points\\\_mean = reviews.points.mean()
				reviews.points.map(lambda p: p - review\\\_points\\\_mean)

			- lambda匿名函数，接收Series里面的每一个值，返回变换后的新值

			- 返回一个全新Series

		### 2. .apply()
			- 作用于整个DataFrame整张表，按行/按列处理。
				def remean\\\_points(row):
    					row.points = row.points - review\\\_points\\\_mean
    					return row

				reviews.apply(remean\\\_points, axis='columns')

			- axis='columns'：逐行处理，函数接收一整行row作为参数

			- axis='index'：逐列处理

			- 返回全新DataFrame

			- 注意：.map()、.apply()都不会修改原数据，原reviews还是原样。

		### 3. pandas内置运算符（向量化运算）
			- pandas支持直接对Series做加减、字符串拼接，速度比map/apply更快。
			- 整列数字直接减去一个数
				reviews.points - review\\\_points\\\_mean

			- 字符串列拼接
				reviews.country + " - " + reviews.region\\\_1

			\*\*优点\*\*：速度快，pandas底层做了加速
			\*\*缺点\*\*：灵活性不如map/apply，写复杂条件逻辑做不到










目前已经开始进行个人项目的学习跟进和书写，但刚开始不乏有很多不足之处，有时即使是跟着步骤做也总出现问题。
比较令我意外的是我经常因为中英文键盘切换不及时而出现问题。
还有其他的，比如说\_\_缩进混乱，函数括号内部遗漏，自主定义解释变量与实际输入不一致这种粗心错误，\_\_
我想我确实把之前学习的一些毛病带到电脑上来了，但我也相信我会逐步改进的。

以及我也在尝试逐步不依靠翻译来写英文标注内容，虽说大部分内容我可以独立完成但不乏\_\_过于口语化和不专业\_\_的描述，这些都是我还需要克服的，
即便完成了雅思考试，英语学习依旧不能懈怠

