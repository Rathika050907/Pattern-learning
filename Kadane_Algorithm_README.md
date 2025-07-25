
# 🚀 Kadane’s Algorithm – Maximum Subarray Sum

## 📘 Problem Statement

> Given an integer array `nums`, find the **contiguous subarray** (containing at least one number) which has the **largest sum**, and return its sum.

---

## 💡 Intuition

Kadane's Algorithm solves the problem in **O(n)** time by iterating through the array just once.

At each index, we decide:
- **Continue** with the existing subarray by adding the current number
- **Start** a new subarray beginning from the current index

We keep updating:
- `max_ending_here`: max sum of subarray ending at current index
- `max_so_far`: overall max subarray sum seen so far

---

## 🧠 Algorithm Steps

1. Initialize:
   ```python
   max_so_far = nums[0]
   max_ending_here = nums[0]
   ```

2. Loop through the array starting from index 1:
   ```python
   for i in range(1, len(nums)):
       max_ending_here = max(nums[i], max_ending_here + nums[i])
       max_so_far = max(max_so_far, max_ending_here)
   ```

3. Return `max_so_far`

---

## 🔍 Dry Run Example

Given:
```text
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

| Index | nums[i] | max_ending_here               | max_so_far |
|-------|---------|-------------------------------|------------|
| 0     | -2      | -2                            | -2         |
| 1     | 1       | max(1, -2 + 1) = 1             | 1          |
| 2     | -3      | max(-3, 1 - 3) = -2            | 1          |
| 3     | 4       | max(4, -2 + 4) = 4             | 4          |
| 4     | -1      | max(-1, 4 - 1) = 3             | 4          |
| 5     | 2       | max(2, 3 + 2) = 5              | 5          |
| 6     | 1       | max(1, 5 + 1) = 6              | 6          |
| 7     | -5      | max(-5, 6 - 5) = 1             | 6          |
| 8     | 4       | max(4, 1 + 4) = 5              | 6          |

✅ Final Result: **6**

Subarray: `[4, -1, 2, 1]`

---

## 🐍 Python Implementation

```python
def kadane(nums):
    max_so_far = nums[0]
    max_ending_here = nums[0]

    for i in range(1, len(nums)):
        max_ending_here = max(nums[i], max_ending_here + nums[i])
        max_so_far = max(max_so_far, max_ending_here)

    return max_so_far

# Example
arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
print("Maximum subarray sum:", kadane(arr))  # Output: 6
```

---

## ☕ Java Implementation

```java
public class KadaneAlgorithm {
    public static int maxSubArray(int[] nums) {
        int max_so_far = nums[0];
        int max_ending_here = nums[0];

        for (int i = 1; i < nums.length; i++) {
            max_ending_here = Math.max(nums[i], max_ending_here + nums[i]);
            max_so_far = Math.max(max_so_far, max_ending_here);
        }

        return max_so_far;
    }

    public static void main(String[] args) {
        int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("Maximum subarray sum: " + maxSubArray(arr)); // Output: 6
    }
}
```

---

## 🧩 Time and Space Complexity

| Aspect             | Value     |
|--------------------|-----------|
| Time Complexity    | `O(n)`    |
| Space Complexity   | `O(1)`    |
| Dynamic Programming| ✅        |
| In-place           | ✅        |

---

## 🌍 Real-Life Analogy

Imagine you are tracking profit/losses over days. Kadane’s Algorithm helps identify the best interval (i.e., buy/sell window) to **maximize total gain**.

---

## 🔗 Related Leetcode Problems

- [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
- [918. Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)
- [152. Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)

---

## 📌 Notes

- Only works on **contiguous subarrays**
- Can be extended to return actual subarray using start/end index tracking
- Handles negative numbers efficiently

---

## 📂 License

This code is licensed under the MIT License.
