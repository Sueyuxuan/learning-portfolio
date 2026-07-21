\# Day 8 - 2026-07-19 - Python Learning



\## 1. 今天学了什么



\- 我终于克服了一部分恐惧然后学习了复杂方程（More Complex Functions）。

\- \*\*More Complex Functions\*\* 可以理解为有很多计算步骤，需要列多个算式，比如下面这个：



```python

def get\_pay(num\_hours):

&#x20;   # Pre-tax pay, based on receiving $15/hour

&#x20;   pay\_pretax = num\_hours \* 15



&#x20;   # After-tax pay, based on being in 12% tax bracket

&#x20;   pay\_aftertax = pay\_pretax \* (1 - .12)



&#x20;   return pay\_aftertax



\# Calculate pay based on working 40 hours

pay\_fulltime = get\_pay(40)

print(pay\_fulltime)

```



\- \*\*Variable Scope（变量作用域）\*\*，分为局部变量和全局变量（以下内容在文中讲解不全面，部分参考了 AI 内容）。

&#x20; - \*\*局部变量（Local Scope）\*\*

&#x20;   - 在函数内部定义的变量，只能在这个函数里面使用，函数外面完全访问不到。

&#x20;   - 只要出了函数，这几个变量就会“消失”，代码找不到它们。

&#x20; - \*\*全局变量（Global Scope）\*\*

&#x20;   - 在所有函数外面定义的变量，整个代码任何地方（函数内、函数外）都能读取。



\- \*\*Multiple Variables（多个变量）\*\*

&#x20; - 设置多个变量时，中间用 `,` 隔开。



```python

def 函数名(变量1, 变量2, 变量3):

```



\- \*\*Functions with No Arguments（无参数函数）\*\*



```python

def 函数名():

&#x20;   print("...")



函数名()

```



即可输出。



\## 2. 有什么问题



\- 、！我终于搞明白那个练习题咋做了，，，虽然还是有点困难吧，毕竟是刚开始做，正确率80%左右，还是要注意一些语言规范。

\- 我翻看之前上传的日志的时候才发现一个问题，大概是说最后一行必须以 "-" 结尾？我没看明白。。。

\- 今天先试一下。

