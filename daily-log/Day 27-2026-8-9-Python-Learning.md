# Day 27-2026-8-9-Python-Learning 代码书写



\#Task1: The type of datas of grade

score=92.5
name="小明"
passed=True

print(type(score))
print(type(name))
print(type(passed))
<class 'float'>
<class 'str'>
<class 'bool'>





\#Task2: The type of datas of family account

s="58.5"
num=float(s)
total=num+41.5
print(total)
100.0





\#Task3: Error on purpose

"100"+50

\---------------------------------------------------------------------------
	TypeError                                 Traceback (most recent call last)
	/tmp/ipykernel\_16/208637779.py in <cell line: 0>()
  		1 # Task3: Error on purpose
      		2 
	----> 3 "100"+50


* TypeError: can only concatenate str (not "int") to str
You can only concatenate strings and strings, not integers and strings directly.

"100" is a string, 50 is an integer. The string is concatenated "+", the number is added, the types are different, Python does not know whether to concatenate or add, and it directly reports an error.

Correct way: int("100")+50







### Notes that I wrote while writing datas, emmmm typing randomly



* An integer is a complete number, which means that they can **count by fingers**, such as the number of cups is three and there's no float, or there's no dot.
* A float is the numbers with a dot, they could be **more specific**, such as the price of goods is 92.5 yuan.
* Strings are texts like this...emmmm there is everything we can print with letters, and they are **enclosed in quotation marks**.
* Bools are like a switch,  which have **only two statements**, turn on and turn off which represent true and false respectively.



* The text "58.5" from receipt is a string.
Even though it looks like a number, Python treats it as plain text. You cannot do math addition directly on strings.
We use float() to convert text‑formatted number into **real numeric value**， so arithmetic calculation can work.



* Why 0.1 + 0.2 is not equal to 0.3?
Floating‑point storage inside computer has tiny precision error
* What is the relationship between bool and if statement?
if judges whether the boolean value is True. Code under if will run only when **condition evaluates to True**.



emmm用英语写还有点不习惯（主要是口语说多了还不习惯正式的书面语，会蹦出来一堆语气词连接句和语法错误），慢慢改吧，可能也是因为我偶尔用语音输入。

