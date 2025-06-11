---
title: "Building a Logic Gate Simulator and Expression Parser"  
date: 2025-06-03  
layout: single  
tags:  
  - algorithms  
  - python  

excerpt: "I created two programs that helped me understand boolean logic and string parsing: a logic gate simulator and a simple expression evaluator."  
---

## Why I studied this  

After working with basic algorithms, I wanted to explore how computers handle logic and mathematical expressions. I was curious about how programming languages evaluate conditions and parse mathematical statements. These two problems gave me hands-on experience with boolean logic and string processing, which are fundamental concepts in programming.  

---

## What I did  

### Problem 1: Logical Gate Simulation  

I needed to simulate compound logic conditions like `(x1 OR x2) AND (x3 OR x4)` using boolean values. This helped me understand how computers process logical operations.  

#### How I approached it:  
I broke down the compound expression into smaller parts and evaluated each step. The key was understanding the order of operations and how AND/OR gates work.  

#### Example walkthrough:  
Given: `(x1 OR x2) AND (x3 OR x4)` where x1=True, x2=False, x3=False, x4=True  
1. First part: (True OR False) = True  
2. Second part: (False OR True) = True  
3. Final result: True AND True = True  

#### Solution Code:  
```python
def logic_gate_simulation(x1, x2, x3, x4):  
    # Evaluate (x1 OR x2)  
    first_part = x1 or x2  
    
    # Evaluate (x3 OR x4)  
    second_part = x3 or x4  
    
    # Combine with AND  
    result = first_part and second_part  
    
    return result  

# Test different combinations  
print("x1=True, x2=False, x3=False, x4=True:")  
print(logic_gate_simulation(True, False, False, True))  # True  

print("x1=False, x2=False, x3=True, x4=False:")  
print(logic_gate_simulation(False, False, True, False))  # False  

# More flexible version  
def evaluate_logic_expression(x1, x2, x3, x4, expression_type):  
    if expression_type == "and_or":  
        return (x1 or x2) and (x3 or x4)  
    elif expression_type == "or_and":  
        return (x1 and x2) or (x3 and x4)  
    
# Examples  
print(evaluate_logic_expression(True, False, False, True, "and_or"))  # True  
print(evaluate_logic_expression(True, False, False, True, "or_and"))  # False  
```

### Problem 2: Binomial Expression Evaluation  

I needed to parse a string like `"3 + 4"` and compute the result based on the operator. This taught me the basics of parsing and evaluating mathematical expressions.  

#### How I approached it:  
I split the string into parts (numbers and operator), then used conditional statements to perform the correct operation based on the operator found.  

#### Example walkthrough:  
Given string: `"7 - 3"`  
1. Split by spaces: ["7", "-", "3"]  
2. Extract: first_number = 7, operator = "-", second_number = 3  
3. Apply operation: 7 - 3 = 4  

#### Solution Code:  
```python
def evaluate_expression(expression):  
    # Split the string by spaces  
    parts = expression.split()  
    
    # Extract the components  
    first_number = int(parts[0])  
    operator = parts[1]  
    second_number = int(parts[2])  
    
    # Perform the operation  
    if operator == "+":  
        result = first_number + second_number  
    elif operator == "-":  
        result = first_number - second_number  
    elif operator == "*":  
        result = first_number * second_number  
    elif operator == "/":  
        result = first_number / second_number  
    else:  
        result = "Unknown operator"  
    
    return result  

# Test examples  
print(evaluate_expression("3 + 4"))    # 7  
print(evaluate_expression("10 - 6"))   # 4  
print(evaluate_expression("5 * 3"))    # 15  
print(evaluate_expression("8 / 2"))    # 4.0  

# Enhanced version with error handling  
def safe_evaluate_expression(expression):  
    try:  
        parts = expression.split()  
        if len(parts) != 3:  
            return "Invalid format. Use: number operator number"  
        
        first_number = float(parts[0])  
        operator = parts[1]  
        second_number = float(parts[2])  
        
        if operator == "+":  
            return first_number + second_number  
        elif operator == "-":  
            return first_number - second_number  
        elif operator == "*":  
            return first_number * second_number  
        elif operator == "/":  
            if second_number == 0:  
                return "Cannot divide by zero"  
            return first_number / second_number  
        else:  
            return f"Unknown operator: {operator}"  
    
    except ValueError:  
        return "Invalid numbers in expression"  

# Test with error cases  
print(safe_evaluate_expression("3 + 4"))        # 7.0  
print(safe_evaluate_expression("10 / 0"))       # Cannot divide by zero  
print(safe_evaluate_expression("abc + 5"))      # Invalid numbers in expression  
```

### Key Insights  

| Problem | What I learned | Main concept |  
|---------|---------------|-------------|
| Logic Gate Simulation | How to combine boolean operations | Breaking complex logic into simple parts |  
| Expression Evaluation | How to parse and process strings | Converting text into actionable operations |  

---

## What I learned  

These problems taught me several important programming concepts:  

- **Boolean logic is everywhere**: Understanding AND, OR, and NOT operations is crucial for making decisions in code  
- **String parsing is powerful**: Breaking down text into meaningful parts is a fundamental skill in programming  
- **Step-by-step evaluation**: Complex expressions can be solved by breaking them into smaller, manageable pieces  
- **Error handling matters**: Real programs need to handle unexpected inputs gracefully  

The logic gate problem helped me understand how computers make decisions, while the expression parser showed me how programming languages process mathematical statements. Both problems reinforced the importance of thinking systematically about problem-solving.  

---

## What I want to do next  

- Build a calculator that can handle more complex expressions with parentheses  
- Learn about parsing more complicated logic expressions with multiple operators  
- Explore how to build simple interpreters for custom languages  
- Practice working with different data types in string parsing  
- Create programs that can evaluate user input in real-time  

---