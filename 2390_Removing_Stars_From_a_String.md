# 2390. Removing Stars From a String

**Difficulty:** Medium  
**Topics:** String, Stack, Simulation

---

## Problem Description

You are given a string `s`, which contains stars `*`.

In one operation, you can:
1. Choose a star in `s`.
2. Remove the closest non-star character to its left, as well as remove the star itself.

Return *the string after all stars have been removed*.

**Note:**
* The input will be generated such that the operation is always possible.
* It can be shown that the resulting string will always be unique.

---

### Examples

#### Example 1:
* **Input:** `s = "leet**cod*e"`
* **Output:** `"lecoe"`
* **Explanation:** Performing the removals from left to right:
  * The closest character to the 1st star is `'t'` in `"leet**cod*e"`. `s` becomes `"lee*cod*e"`.
  * The closest character to the 2nd star is `'e'` in `"lee*cod*e"`. `s` becomes `"lecod*e"`.
  * The closest character to the 3rd star is `'d'` in `"lecod*e"`. `s` becomes `"lecoe"`.
  * There are no more stars, so we return `"lecoe"`.

#### Example 2:
* **Input:** `s = "erase*****"`
* **Output:** `""`
* **Explanation:** The entire string is removed, so we return an empty string.

---

### Constraints:
* `1 <= s.length <= 10^5`
* `s` consists of lowercase English letters and stars `*`.
* The operation above can be performed on `s`.

---

## Solution Approach

This problem can be elegantly solved using a **Stack** data structure (or a `StringBuilder` acting as a stack in Java). 

### Intuition:
* As we iterate through the string from left to right, we encounter normal lowercase characters and stars (`*`).
* A star acts like a **backspace** key: it deletes the most recently added character to its left.
* This "Last-In, First-Out" (LIFO) behavior perfectly maps to a Stack.
* If the character is a letter, we push it onto the stack.
* If the character is a star `*`, we pop the top character off the stack.

---

## Java Source Code

```java
class Solution {
    public String removeStars(String s) {
        // StringBuilder acts as a stack to efficiently build the final string
        StringBuilder stack = new StringBuilder();

        for (char c : s.toCharArray()) {
            if (c == '*') {
                // Remove the last appended character (closest non-star to the left)
                stack.deleteCharAt(stack.length() - 1);
            } else {
                // Append lowercase English letters
                stack.append(c);
            }
        }

        return stack.toString();
    }
}