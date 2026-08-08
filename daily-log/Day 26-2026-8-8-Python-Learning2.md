# Day 26-2026-8-8-Python-Learning 代码书写



# Task1: Caculte total cost of goods

def total\_cost(price,quantity):
return price\*quantity

# 3 cups of milktea and each is 18 yuan

result1=total\_cost(18,3)
print(result1)
54





# Task2: Caculte calories burned from training

def calories(minutes):
return minutes\*10

result2=calories(45)
print(result2)
450





# Task3: Caculte the total travel budget

def trip\_budget(days,hotel\_per\_night,flight\_ticket):
return (days-1)\*hotel\_per\_night+flight\_ticket

result3=trip\_budget(5,350,800)
print(result3)
2200





# Task3: Caculte the total travel budget

def trip\_budget(days,hotel\_per\_night,flight\_ticket):

&#x20;   # For convenience and in case of mistakes,we can change "day-1"into night
    night=days-1
    return night\*hotel\_per\_night+flight\_ticket


result3=trip\_budget(5,350,800)
print(result3)
2200





，，，，我还是没找到怎么复原，可能是我保存的路径有点问题直接找不到了
下次写的时候可以先在\*\*“我的笔记”\*\*里面新建笔记再写，比直接create风险小
所以我还是重写了一遍

但介于上次写的没有运行，这次写还是找到了一个令人意外的问题，就是**函数后面忘加“：”**
这也不是通病，因为是偶尔忘记，但还是要注意一下，不要只靠报错来发现问题（虽然这也不是不行）



然后还借鉴了一些参考代码，我发现我们之间的一些区别
参考代码可能会有意识地去**简化一些长式子**来规避一些不必要的麻烦，以及防止符号丢失导致的计算错误
比如Task3的第二版，参考代码把"day-1"改为了night并用此替换，可能在目前这种简单代码中无所谓，但以后随着代码逐渐复杂，这种简化可以起到很大的作用

我也反思了一下自己，由于之前长时间的无论是体制内还是al的数学学习，我也是习惯于长式子，一步到位，但这同时也会带来“一个式子出问题毁全篇”的风险。
所以我还是最好趁着难度还没上来，有意识地去简化和分步

