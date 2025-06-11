---
title: "Understanding Basic Sorting Algorithms: Bubble, Selection, and Insertion Sort"  
date: 2025-06-01  
layout: single  
tags:  
  - algorithms  
  
  - python  

excerpt: "I explored three fundamental sorting algorithms to understand how lists work and gained my first real introduction to algorithmic thinking."  
---

## Why I studied this  

As I continue learning programming, I realized I needed to understand algorithms better. Sorting seemed like a perfect starting point since it's something we do naturally - organizing books, arranging numbers, sorting files. I wanted to see how computers approach this basic task and use it as my introduction to algorithmic thinking. Understanding how sorting works also helped me grasp how lists and arrays function under the hood.  

---

## What I did  

### What are Sorting Algorithms?  

Sorting algorithms are step-by-step procedures for arranging elements in a specific order (usually ascending or descending). While Python has built-in sorting functions, learning these basic algorithms taught me how to think systematically about problem-solving.  

### Bubble Sort  
Bubble sort repeatedly compares adjacent elements and swaps them if they're in the wrong order. It's called "bubble" because smaller elements "bubble up" to the beginning of the list.  

#### How it works:  
1. Compare first two elements  
2. Swap if the first is larger than the second  
3. Move to the next pair  
4. Repeat until no swaps are needed  

#### Example Code:  
```python
def bubble_sort(arr):  
    n = len(arr)  
    for i in range(n):  
        for j in range(0, n - i - 1):  
            if arr[j] > arr[j + 1]:  
                arr[j], arr[j + 1] = arr[j + 1], arr[j]  
    return arr  

# Example  
numbers = [64, 34, 25, 12, 22, 11, 90]  
print("Original:", numbers)  
print("Sorted:", bubble_sort(numbers.copy()))  
# Output: [11, 12, 22, 25, 34, 64, 90]  
```

### Selection Sort  
Selection sort finds the smallest element and moves it to the beginning, then finds the second smallest, and so on.  

#### How it works:  
1. Find the minimum element in the unsorted portion  
2. Swap it with the first unsorted element  
3. Move the boundary of the sorted portion one position right  
4. Repeat until the entire list is sorted  

#### Example Code:  
```python
def selection_sort(arr):  
    n = len(arr)  
    for i in range(n):  
        min_idx = i  
        for j in range(i + 1, n):  
            if arr[j] < arr[min_idx]:  
                min_idx = j  
        arr[i], arr[min_idx] = arr[min_idx], arr[i]  
    return arr  

# Example  
numbers = [64, 34, 25, 12, 22, 11, 90]  
print("Original:", numbers)  
print("Sorted:", selection_sort(numbers.copy()))  
# Output: [11, 12, 22, 25, 34, 64, 90]  
```

### Insertion Sort  
Insertion sort builds the sorted list one element at a time by inserting each element into its correct position among the already sorted elements.  

#### How it works:  
1. Start with the second element (assume first is sorted)  
2. Compare it with elements in the sorted portion  
3. Shift larger elements to the right  
4. Insert the current element in the correct position  
5. Repeat for all remaining elements  

#### Example Code:  
```python
def insertion_sort(arr):  
    for i in range(1, len(arr)):  
        key = arr[i]  
        j = i - 1  
        while j >= 0 and arr[j] > key:  
            arr[j + 1] = arr[j]  
            j -= 1  
        arr[j + 1] = key  
    return arr  

# Example  
numbers = [64, 34, 25, 12, 22, 11, 90]  
print("Original:", numbers)  
print("Sorted:", insertion_sort(numbers.copy()))  
# Output: [11, 12, 22, 25, 34, 64, 90]  
```

### Comparison of the Three Methods  

| Algorithm      | Best Case | Average Case | Worst Case | Memory | When to Use |  
|----------------|-----------|--------------|------------|---------|-------------|
| Bubble Sort    | O(n)      | O(n²)        | O(n²)      | O(1)    | Never in practice, good for learning |  
| Selection Sort | O(n²)     | O(n²)        | O(n²)      | O(1)    | When memory writes are expensive |  
| Insertion Sort | O(n)      | O(n²)        | O(n²)      | O(1)    | Small datasets or nearly sorted data |  

---

## What I learned  

These sorting algorithms gave me crucial insights into how lists work and introduced me to algorithmic thinking:  

- **Lists are dynamic**: I learned how elements can be moved around and how indices change during operations  
- **Efficiency matters**: Even simple tasks can be done in multiple ways with different performance characteristics  
- **Step-by-step thinking**: Algorithms break complex problems into simple, repeatable steps  
- **Trade-offs exist**: Each algorithm has strengths and weaknesses depending on the situation  

Bubble sort taught me about comparison-based sorting, selection sort showed me the power of finding extremes, and insertion sort demonstrated how to build solutions incrementally. While these aren't the fastest sorting methods, they helped me understand the fundamental concepts that more advanced algorithms build upon.  

---

## What I want to do next  

- Implement merge sort and quick sort to see more efficient approaches  
- Visualize these sorting algorithms to better understand their behavior  
- Practice analyzing time and space complexity for different algorithms  
- Apply these problem-solving patterns to other algorithmic challenges  
- Explore when Python's built-in `sorted()` function uses different algorithms internally  

---