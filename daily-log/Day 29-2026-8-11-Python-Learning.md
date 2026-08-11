# Day 29-2026-8-11-Python-Learning 代码书写

## 今日代码书写任务（含之前学习的内容总结）
1. 建一个列表存7天开销（数字自己编）。
2. 写函数 week_report(spend_list, budget)：算总支出和日均支出；如果总支出超过 budget，返回“超支了 X 元”，否则返回“还剩 X 元”。
3. 用两组不同的数据调用它，验证两个分支都能走到。



def week_report(spend_list, budget):

    #Calculate total spending

    total = sum(spend_list)

    #Calculate average daily spending

    avg_spend = total / len(spend_list)
    print(f"Total spending this week: {total} USD, average daily spending: {avg_spend:.2f} USD")

    if total > budget:
        over_amount = total - budget
        return f"Over budget by {over_amount} USD"
    else:
        remain_amount = budget - total
        return f"{remain_amount} USD left"


#Test case 1: 7‑day spending data, budget = 500
spend1 = [60, 85, 42, 90, 78, 55, 63]
result1 = week_report(spend1, 500)
print(result1)
print("-" * 30)

#Test case 2: 7‑day spending data, budget = 400 (over‑budget scenario)
spend2 = [80, 95, 66, 72, 88, 91, 75]
result2 = week_report(spend2, 400)
print(result2)




Total spending this week: 473 USD, average daily spending: 67.57 USD
27 USD left
------------------------------
Total spending this week: 567 USD, average daily spending: 81.00 USD
Over budget by 167 USD






#### 用到的知识点简要回顾
- For this budget‑tracking tool, I worked with: lists to store 7‑day spend data, sum() to get total cost, self‑made functions to wrap all calculations, if‑else to check if we go over budget, and formatted strings for cleaner print output.



#### 写代码遇到的bug以及解决办法

- 搞混了 return 和 print
I only put print() inside my function. When I called the function, my variable just got None, not the message I wanted.
Realized print just shows text on screen. return actually sends the result back. So I used return for the message as the task asked.

- 计算平均值直接写死数字7
I wrote total /7. If my list changed length, the whole code would break. Not flexible at all.
 Used len(spend_list) instead. It grabs the real length of my list automatically.

- 输出一堆乱七八糟的小数
After division, I got super long messy decimals, hard to read.
Used f‑string :.2f to keep only two decimal places.



#### 两组数据集测试验证
- Test 1: spend list [60, 85, 42, 90, 78, 55, 63], budget = 500 → stayed under budget, 27 USD left.
- Test 2: spend list [80, 95, 66, 72, 88, 91, 75], budget = 400 → went over budget, overspent 167 USD.
- Both code branches work as expected.
