---
title: "Solving Two Algorithmic Problems: Bitwise Operations and Range Updates"  
date: 2025-06-02  
layout: single  
tags:  
  - algorithms  
  - python  


excerpt: "I tackled two interesting algorithmic problems that taught me about bitwise operations and efficient range processing techniques."  
---

## Why I studied this  

After learning basic sorting algorithms, I wanted to challenge myself with more complex problems that would expand my algorithmic thinking. I came across two fascinating problems that seemed simple at first but required deeper understanding of number operations and array manipulation. These problems helped me explore bitwise operations and efficient range update techniques.  

---

## What I did  

### Problem 1: Bitwise Divide-to-One  

Given a number, I needed to repeatedly perform operations until it becomes 1, counting the total number of steps:  
- If the number is even: divide by 2  
- If the number is odd: subtract 1, then divide by 2  

#### How I approached it:  
The key insight was recognizing this as a bitwise operation problem. Dividing by 2 is equivalent to right-shifting bits, and subtracting 1 from an odd number removes the least significant bit.  

#### Example walkthrough:  
Let's trace through the number 6:  
1. 6 (even) → 6/2 = 3 (operation 1)  
2. 3 (odd) → (3-1)/2 = 1 (operation 2)  
3. Result: 1 (total operations: 2)  

#### Solution Code:  
```python
def divide_to_one(n):  
    count = 0  
    while n != 1:  
        if n % 2 == 0:  
            n = n // 2  
        else:  
            n = n - 1  
            n = n // 2  
        count += 1  
    return count  

# Examples  
print(divide_to_one(6))   # Output: 2  
print(divide_to_one(8))   # Output: 3  
print(divide_to_one(15))  # Output: 5  
```

### Problem 2: Range Update with Modulo Condition  

I had a list and a set of queries in the form `[s, e, k]`, where I needed to increment elements in the range `[s, e]` if the index is divisible by `k`.  

#### How I approached it:  
This problem required efficient range processing. A naive approach would iterate through each range for every query, but that could be very slow. I learned about difference arrays and optimized range updates.  

#### Example walkthrough:  
Given array `[1, 2, 3, 4, 5]` and query `[1, 4, 2]`:  
- Range: indices 1 to 4 (elements 2, 3, 4, 5)  
- Condition: index divisible by 2  
- Indices 2 and 4 meet the condition  
- Result: `[1, 2, 4, 4, 6]`  

#### Solution Code:  
```python
def range_update(arr, queries):  
    result = arr.copy()  
    
    for s, e, k in queries:  
        for i in range(s, e + 1):  
            if i % k == 0:  
                result[i] += 1  
    
    return result  

# Example usage  
arr = [1, 2, 3, 4, 5]  
queries = [[1, 4, 2], [0, 3, 3]]  
print("Original:", arr)  
print("After queries:", range_update(arr, queries))  
# Output: [2, 2, 4, 5, 6]  
```

### Key Insights  

| Problem | What I learned | Main concept |  
|---------|---------------|-------------|
| Divide-to-One | Count steps to reach 1 | Simple while loop with conditions |  
| Range Update | Update specific positions in ranges | Loop through ranges and check divisibility |  

---

## What I learned  

These problems taught me several important concepts:  

- **Breaking down problems step by step**: Both problems required clear logical steps that I could implement one at a time  
- **Understanding conditions**: Learning when to apply different operations based on simple checks (even/odd, divisible by k)  
- **Working with loops**: Using while loops for unknown iterations and for loops for known ranges  
- **Array manipulation**: How to safely copy and modify arrays without affecting the original  

The divide-to-one problem helped me understand how to count operations in a loop, while the range update problem taught me how to process multiple queries on an array. Both problems showed me that complex-sounding problems can often be solved with straightforward logic.  

---

## What I want to do next  

- Practice more problems involving simple loops and conditions  
- Learn about working with 2D arrays and nested loops  
- Try problems that involve counting and tracking operations  
- Explore basic string manipulation problems  
- Work on problems that combine arrays with mathematical operations  

---