---
program: "Python and AI Essentials"
module: "Build reusable Python components"
module_order: 5
topic: "Design useful functions"
topic_order: 1
topic_id: "05-01"
content_status: "complete"
reviewed_on: "2026-10-05"
---


# Design useful functions

Both the receipt and the daily report calculate quantity times price. Keeping two separate copies of the rule makes updates risky. A function gives that calculation one reusable definition.

## What you will be able to do

- Create a function with clear inputs and a return value
- Call it using positional, keyword, and default arguments

## Separate a definition from a call

```python
def calculate_total(quantity, unit_price=8):
    return quantity * unit_price

print(calculate_total(3))
print(calculate_total(3, 6))
print(calculate_total(unit_price=6, quantity=4))
```

Expected output:

```text
24
18
24
```

`def` defines the function. `quantity` and `unit_price` are parameters: names used within the definition. The values supplied by a call are arguments. The body runs when the function is called, not merely because Python reads its definition.

The first call uses the default price of 8. The second matches arguments by position. The third matches by keyword, so its order is explicit. Positional arguments generally precede keyword arguments in a call. Supplying the same parameter twice or omitting a required argument raises `TypeError`.

## Return a result rather than only displaying it

`return` sends a value back to the caller and ends that function call. The caller can print it, compare it, or use it in another calculation.

```python
def calculate_total(quantity, unit_price):
    return quantity * unit_price

subtotal = calculate_total(3, 8)
delivery_fee = 5
print(subtotal + delivery_fee)
```

Expected output:

```text
29
```

Printing inside a function displays information but does not automatically return it. A function that reaches its end without an explicit value-returning `return` returns `None`. Keep calculations separate from presentation when you want to reuse them in different contexts.

## Make the responsibility small

A function named `calculate_total` should calculate a total. If it also asks for input, writes a file, and sends a message, it becomes harder to test and reuse. Small responsibilities give errors a narrower place to hide.

Functions reduce duplication, let you describe work through meaningful names, and make it possible to check one piece independently. They are useful even before a program becomes large.

## Practice: calculate a delivery fee

Define `delivery_fee(subtotal, threshold=30)`. Return 0 when the subtotal is at least the threshold; otherwise return 5. Test 29, 30, and 31.

### Check your work

```python
def delivery_fee(subtotal, threshold=30):
    if subtotal >= threshold:
        return 0
    return 5

for subtotal in [29, 30, 31]:
    print(delivery_fee(subtotal))
```

Expected output:

```text
5
0
0
```

The second return is reached only when the earlier branch does not return. That makes an `else` unnecessary here, although including one would also be valid.

## Quick check

A function prints 24 but has no return statement. What is stored by `result = function_call()`?

### Answer and explanation

`None`. Displayed output and returned values are separate. Return 24 if the caller needs that value.

## Take this forward

Define the inputs, the result, and the responsibility before writing a function. Next, you will manage names and flexible argument lists.

## References and further reading

- [Python control flow and functions](https://docs.python.org/3/tutorial/controlflow.html)
- [Python built-in functions](https://docs.python.org/3/library/functions.html)
