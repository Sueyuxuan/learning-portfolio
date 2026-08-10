# Day 28-2026-8-10-Python-Learning 代码书写



\#Task1: Family account

daily\_spend=\[45,120,38,260,55,80,95]

total=sum(daily\_spend)
max\_spend=max(daily\_spend)
avg\_spend=sum(daily\_spend)/len(daily\_spend)

print(total)
print(max\_spend)
print(avg\_spend)

693
260
99.0





\#Task1: Family account

daily\_spend=\[45,120,38,260,55,80,95]

total=sum(daily\_spend)
max\_spend=max(daily\_spend)
avg\_spend=sum(daily\_spend)/len(daily\_spend)

\#We can do it more clearly

print(f"Total:{total}")
print(f"Max:{max\_spend}")
print(f"Average:{avg\_spend}")

Total:693
Max:260
Average:99.0





\#Task2: Travel

cities=\["Chengdu","Chongqing","Xian"]

first=cities\[0]
last=cities\[-1]
cities.append("Taian")

print(f"First stop:{first}")
print(f"Last stop:{last}")
print(f"Updated city lisit:{cities}")

First stop:Chengdu
Last stop:Xian
Updated city lisit:\['Chengdu', 'Chongqing', 'Xian', 'Taian']





\#Task3: Family account(with error)

daily\_spend=\[45,120,38,260,55,80,95]

find=daily\_spend\[7]

print(find)

IndexError                                Traceback (most recent call last)
/tmp/ipykernel\_16/2567826119.py in <cell line: 0>()
3 daily\_spend=\[45,120,38,260,55,80,95]
4
----> 5 find=daily\_spend\[7]
6
7 print(find)



\---

#### IndexError: list index out of range.

The list contains 7 items. Since list indexes **start at 0**, the largest available index is 6. Index  7  is beyond the list boundary and does not exist.
概括一下就是，从前面学习的内容可以得知，列表从0开始计数，也就是说包含七个内容的列表范围是0到6,7已经超出范围



#### 关于列表的一些注意事项

- A list can store related data in the **same container**. It supports batch calculation and iteration and keeps code clean.


- Lists can contain different types of datas at the same time. But this may make data-analysis fail to work,such as max() and sum().



