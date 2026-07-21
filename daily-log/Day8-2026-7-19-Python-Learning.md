Day8-2026-7-19-Python-Learning



\## 1. 今天学了什么

\-我终于克服了一部分恐惧然后学习了复杂方程（more complex function）

\-More complex function, 可以理解为有很多条件，需要列多个算式，比如下面这个

&#x09;-def get\_pay(num\_hours):

Functions with no argumentsFunctions with no arguments

&#x20;          #Pre-tax pay, based on receiving $15/hour

&#x20; 	    pay\_pretax = num\_hours \* 15       // 算式1



&#x20;  	    #After-tax pay, based on being in 12% tax bracket

&#x20;     	    pay\_aftertax = pay\_pretax \* (1 - .12)    //算式2

&#x20;  	    return pay\_aftertax



&#x09;    #Calculate pay based on working 40 hours

&#x20;          pay\_fulltime = get\_pay(40)

&#x20;          print(pay\_fulltime)

\-Variable scope 变量范围，分为局部变量和全局变量（以下内容在文中讲解不全面，部分参考了ai内容）

&#x09;-局部变量 local scope

&#x09; 在函数内部定义的变量，只能在这个函数里面使用，函数外面完全访问不到。

&#x20;        只要出了函数，这几个变量直接“消失”，代码找不到它们。

&#x09;-全局变量 global scope

&#x20;        在所有函数外面定义的变量，整个代码任何地方（函数内、函数外）都能读取。

\-Multiple variables 多变量，在设置多变量时，中间用“，”隔开

&#x20;	def 函数名（变量1，变量2，变量3）:

\-Functions with no arguments 无变量函数

&#x09;def 函数名（）：

&#x09;print（“...”）

&#x09;

&#x09;函数名（）//即可输出



\## 2. 有什么问题

\-、！我终于搞明白那个练习题咋做了，，，虽然还是有点困难吧，毕竟是刚开始做，正确率80%左右，还是要注意一些语言规范

\-我翻看之前上传的日志的时候才发现一个问题，大概是说最后一行必须以“-”结尾？我没看明白。。。

\-今天先试一下

