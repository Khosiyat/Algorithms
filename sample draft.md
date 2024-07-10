# Sliding Window Problem for Absolute Beginners

## Introduction

The sliding window problem is a common technique used in programming to solve problems related to sequences (like arrays or strings). The goal is to find a subset of the sequence that satisfies certain conditions. 

To make it easier to understand, we'll break it down using simple analogies and examples from everyday life.

<details>
    <summary>Everyday Analogies</summary>

### 1. Watching a Movie

Imagine you have a movie that is 2 hours long. You want to find the most interesting 10-minute segment. You start watching from the beginning and keep a record of how interesting each part is. As you move forward in the movie, you always have a 10-minute window in your mind and adjust it until you find the most interesting segment.

### 2. Reading a Book

Think of reading a book where you want to remember the most exciting chapter. Instead of reading the entire book again, you remember a window of 3 pages at a time. As you read, you update your memory with the excitement level of the new page and forget the least exciting part of the previous pages in your window.

### 3. Shopping

Imagine you are at a market, and you want to find the cheapest combination of 3 items from a list of items with different prices. You start with the first 3 items, calculate their total price, and then move your window of 3 items forward, adjusting the total price as you add a new item and remove the old one.

</details>

<details>
    <summary>Breaking Down the Problem</summary>

Let's break down the problem we are solving: finding the maximum sum of a subarray of size `k`.

### Problem Explanation

Given an array of integers and an integer `k`, our goal is to find the maximum sum of any subarray of size `k`.



Code Explanation
Initialization

```
start, end = 0, 0
current_sum = 0
```

We start by setting start and end pointers to 0 and current_sum to 0.

Main Loop

```
while end < len(arr):
    current_sum += arr[end]
    end += 1
```

We iterate through the array using the end pointer. For each position of end, we add the current element to current_sum and move end one step to the right.

Adjusting the Window

```
while end - start >= k:
    current_sum -= arr[start]
    start += 1
```
When the size of the window (difference between end and start) reaches k, we adjust the window by subtracting the element at the start pointer from current_sum and moving start one step to the right.

Returning the Result

```
return current_sum
```

Finally, we return the current_sum which represents the sum of the maximum sum subarray of size k.

Example Usage
Let's see how this works with our example array [1, 4, 2, 7, 3, 6, 5] and k = 3.

Start with `start = 0`, `end = 0`, `current_sum = 0`.
Move `end` to the right and keep adding to `current_sum` until `end - start >= k`.
Adjust the window by moving `start` to the right and subtracting from `current_sum`.
Continue this process until end reaches the end of the array.
The output will be:


- The maximum sum subarray of size 3 is: 15
This means the subarray [7, 3, 6] has the maximum sum of 15.

Conclusion
The sliding window technique is a powerful tool for solving problems involving sequences. By understanding how to adjust the window dynamically, you can solve many problems efficiently. Use the analogies and code breakdown provided to grasp the concept and apply it to different scenarios.

For example, in the array `[1, 4, 2, 7, 3, 6, 5]` with `k = 3`, we want to find the subarray of 3 consecutive elements that has the highest sum.

</details>


<details>
    <summary>Steps to Solve</summary>

1. Initialize two pointers, `start` and `end`, both set to the beginning of the array.
2. Use a variable `current_sum` to keep track of the sum of the current window.
3. Move the `end` pointer to the right, adding elements to `current_sum`.
4. Once the window size reaches `k`, adjust the window by moving the `start` pointer to the right, subtracting elements from `current_sum`.
5. Continue this process until the `end` pointer reaches the end of the array.

</details>


<details>
    <summary>Full Code BLock</summary>

```python
def sliding_window_problem(arr, k):
    start, end = 0, 0
    current_sum = 0

    while end < len(arr):
        # Perform operations based on the current window [start, end]
        current_sum += arr[end]

        # Adjust the window by moving the pointers
        end += 1

        # Check if the window needs to be adjusted further and move the start pointer
        while end - start >= k:
            # Update the window based on the removal of the element at the start pointer
            current_sum -= arr[start]
            start += 1

    return current_sum
```

# Example usage
- arr = [1, 4, 2, 7, 3, 6, 5]
- k = 3
- result = sliding_window_problem(arr, k)
- print(f"The maximum sum subarray of size {k} is: {result}")

</details>




<details>
    <summary>Try Yourself! Submit Your Code!</summary>

```python











```

### SUBMIT BUTTON

</details>
