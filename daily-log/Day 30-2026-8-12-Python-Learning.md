# Day 30-2026-8-12-Python-Learning 代码书写





#Task 1: consumption example, round()
help(round)
expense = 58.667
round_int = round(expense)
round_1dp = round(expense, 1)
print(f"Round to integer: {round_int}")
print(f"Round to 1 decimal place: {round_1dp}")



Help on built-in function round in module builtins:

round(number, ndigits=None)
    Round a number to a given precision in decimal digits.

    The return value is an integer if ndigits is omitted or None.  Otherwise
    the return value has the same type as the number.  ndigits may be negative.

Round to integer: 59
Round to 1 decimal place: 58.7







#Task 2: grade() function with docstring
def grade(score):
    """
    Give a grade based on input score.
    :param score: int or float, student's test score
    :return: str, corresponding grade level
    """
    if score >= 80:
        return "A"
    elif score >= 60:
        return "B"
    else:
        return "C"

help(grade)



Help on function grade in module __main__:

grade(score)
    Give a grade based on input score.
    :param score: int or float, student's test score
    :return: str, corresponding grade level








#Task3: discount_price with default argument
def discount_price(price, rate=0.9):
    """
    Calculate price after discount.
    :param price: original price
    :param rate: discount factor, default value 0.9 (10% off)
    :return: price after discount
    """
    return price * rate


#call with default 90% price
res_default = discount_price(100)
# call with 70% price
res_70 = discount_price(100, 0.7)

print(f"Default discount(90%): {res_default}")
print(f"70% discount(7%): {res_70}")




Default discount(90%): 90.0
70% discount(7%): 70.0




### Help的作用
- I don’t need to **memorize every function** by heart. When I forget how a function works, help() pulls up its built‑in docs. I can quickly check parameters and return values.

### 用折扣例子说明默认参数的行为
- For default parameters: if you skip that argument, the function uses its preset default value. If you pass in a value, it overwrites the default.
Example from discount_price(price, rate=0.9)
‑ discount_price(100): no rate given → uses built‑in 0.9 for 10% off.
‑ discount_price(100,0.7): I give rate=0.7, so it replaces the default and gives 30% off.

### 一些我踩过or常见的坑
- help(round()) with extra parentheses. It runs round() first, then asks help for its output value, not for the round function itself. **Correct: help(round).**
- Default‑value parameters cannot go before normal required parameters, otherwise Python throws an error.

