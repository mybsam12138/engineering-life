# HackerRank-Style Mock Technical Assessment

This mock test is designed to feel close to a typical HackerRank screening for a Java backend candidate.  
Focus on:
- correctness
- clear thinking
- handling edge cases
- writing code you can explain later

---

## Test Rules

- Time limit: **75 minutes**
- Suggested structure:
  - **Question 1 (MCQ): 10 minutes**
  - **Question 2 (SQL): 15 minutes**
  - **Question 3 (Coding Easy/Medium): 20 minutes**
  - **Question 4 (Coding Medium): 30 minutes**
- Preferred language for coding: **Java**
- Try to solve without looking up answers first.
- After finishing, review:
  - null / empty input
  - boundary cases
  - time complexity
  - readability

---

# Part 1 — Multiple Choice

Choose the **best** answer.

## Q1. Java HashMap
What is the average time complexity of `put()` and `get()` in a Java `HashMap`?

A. `O(n)`  
B. `O(log n)`  
C. `O(1)`  
D. `O(n log n)`

---

## Q2. String Immutability
Which statement about Java `String` is correct?

A. `String` is mutable, so methods like `replace()` modify the original object  
B. `String` is immutable, so methods like `replace()` return a new object  
C. `String` is mutable only inside loops  
D. `String` can only be changed by using `final`

---

## Q3. SQL GROUP BY
Which clause is used to filter grouped records after aggregation?

A. `WHERE`  
B. `ORDER BY`  
C. `HAVING`  
D. `LIMIT`

---

## Q4. Java Collection Choice
Which data structure is most suitable if you need:
- fast membership lookup
- no duplicate elements

A. `ArrayList`  
B. `LinkedList`  
C. `HashSet`  
D. `TreeMap`

---

## Q5. Exception Handling
Which statement is correct?

A. `RuntimeException` must always be declared with `throws`  
B. Checked exceptions must be handled or declared  
C. `NullPointerException` is a checked exception  
D. `Error` should usually be caught in business code

---

# Part 2 — SQL

## Question
You are given the following `orders` table:

| order_id | customer_id | amount | status     | created_at  |
|---------:|------------:|-------:|------------|-------------|
| 1        | 101         | 120    | PAID       | 2026-03-01  |
| 2        | 101         | 80     | CANCELLED  | 2026-03-03  |
| 3        | 102         | 200    | PAID       | 2026-03-04  |
| 4        | 103         | 150    | PAID       | 2026-03-06  |
| 5        | 101         | 90     | PAID       | 2026-03-08  |
| 6        | 102         | 60     | PAID       | 2026-03-09  |

Write an SQL query to find:

- each `customer_id`
- total paid amount
- number of paid orders

Only include customers whose **total paid amount is greater than 150**.

Sort the result by `total_paid` descending.

### Expected columns
- `customer_id`
- `total_paid`
- `paid_order_count`

---

# Part 3 — Coding Question 1

## Problem: Two Sum

Given an integer array `nums` and an integer `target`, return the **indices** of the two numbers such that they add up to `target`.

You may assume that:
- each input has exactly one solution
- you may not use the same element twice

### Example 1
```text
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
```

### Example 2
```text
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

### Function signature
```java
public int[] twoSum(int[] nums, int target)
```

### What interviewer may check
- correct use of `HashMap`
- time complexity
- duplicate handling
- whether you return indices rather than values

---

# Part 4 — Coding Question 2

## Problem: First Non-Repeating Character

Given a string `s`, return the index of the **first non-repeating character**.  
If it does not exist, return `-1`.

### Example 1
```text
Input: s = "leetcode"
Output: 0
```

### Example 2
```text
Input: s = "loveleetcode"
Output: 2
```

### Example 3
```text
Input: s = "aabb"
Output: -1
```

### Function signature
```java
public int firstUniqChar(String s)
```

### What interviewer may check
- frequency counting
- handling empty string
- clear two-pass logic
- time complexity `O(n)`

---

# Answer Section

## Part 1 — Multiple Choice Answers

### Q1
**Answer: C**

Reason: average-case `put()` and `get()` in `HashMap` are typically `O(1)`.

### Q2
**Answer: B**

Reason: `String` is immutable in Java. Methods like `replace()` return a new string.

### Q3
**Answer: C**

Reason: `HAVING` filters groups after aggregation.

### Q4
**Answer: C**

Reason: `HashSet` gives fast lookup and automatically removes duplicates.

### Q5
**Answer: B**

Reason: checked exceptions must be caught or declared.

---

## Part 2 — SQL Answer

```sql
SELECT
    customer_id,
    SUM(amount) AS total_paid,
    COUNT(*) AS paid_order_count
FROM orders
WHERE status = 'PAID'
GROUP BY customer_id
HAVING SUM(amount) > 150
ORDER BY total_paid DESC;
```

### Expected result from the sample data

| customer_id | total_paid | paid_order_count |
|------------:|-----------:|-----------------:|
| 102         | 260        | 2                |
| 101         | 210        | 2                |

---

## Part 3 — Coding Question 1 Answer

```java
import java.util.HashMap;
import java.util.Map;

public class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }

        return new int[0];
    }
}
```

### Why this is good
- time complexity: `O(n)`
- space complexity: `O(n)`
- standard HackerRank / interview solution
- easy to explain

---

## Part 4 — Coding Question 2 Answer

```java
public class Solution {
    public int firstUniqChar(String s) {
        if (s == null || s.length() == 0) {
            return -1;
        }

        int[] freq = new int[26];

        for (int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
        }

        for (int i = 0; i < s.length(); i++) {
            if (freq[s.charAt(i) - 'a'] == 1) {
                return i;
            }
        }

        return -1;
    }
}
```

### Why this is good
- time complexity: `O(n)`
- space complexity: `O(1)` because array size is fixed
- simple and readable
- easy to defend in an interview

---

# Self-Review Checklist

Before you consider yourself done, check:

- Did I handle null or empty input?
- Did I choose the right data structure?
- Can I explain the time complexity clearly?
- Is my code readable?
- If the interviewer asks me to optimize, do I know why this is already efficient?

---

# Bonus Follow-Up Questions

These are very common after you finish coding.

## For Two Sum
1. Why use `HashMap` instead of two nested loops?
2. What is the time complexity of your solution?
3. What happens if there are duplicate numbers?
4. What if the problem asks for values instead of indices?

## For First Non-Repeating Character
1. Why do you need two passes?
2. Can this work for uppercase letters too?
3. What would you change if the input contains all ASCII characters?
4. What is the trade-off between `HashMap<Character, Integer>` and `int[]`?

---

# Suggested Scoring

- Multiple choice: **5 points**
- SQL: **15 points**
- Coding Question 1: **35 points**
- Coding Question 2: **45 points**

### Rating guide
- **85–100**: strong pass
- **70–84**: probably pass for many backend screenings
- **50–69**: borderline
- **Below 50**: needs more practice

---

# Next Practice Direction

If this felt manageable, next you should practice:
1. `Valid Parentheses`
2. `Merge Intervals`
3. `Top N salary` SQL
4. `Group By + Having`
5. `Sliding Window` basics

