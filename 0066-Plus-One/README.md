# Plus One

Link https://leetcode.com/problems/plus-one/

Difficulty: Easy

## Question:

Given a **non-empty** array of digits representing a non-negative integer, plus one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

**Example 1:**

```
Input: [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

**Example 2:**
```
Input: [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
```

## Analysis:

此题主要是 **进位** 问题

1. 如果末位（个位）小于 9，那么直接将末位 +1 返回即可
2. 如果末位（个位）等于 9，将该为这设置成 0，并且产生了进位，那么接下来观察下一位
  1. 如果前一位（十位）小于 9 ，直接十位加 1 返回即可
  2. 如果前一位（十位）等于 9，将该位（十位）设置为 0 ，并且产生了进位，接下来观察前一位（百位）
3. 以此类推，最后运算完查看第一位是否为 0，如果是 0，则在数组前面插入一个 1

空间复杂度 O(1)

时间复杂度 O(n)

## JavaScript

```JavaScript
const plusOne = function(digits) {
  let length = digits.length
  while (length--) {
    if (digits[length] < 9) {
      digits[length]++
      return digits
    }
    digits[length] = 0
  }
  digits.unshift(1)
  return digits
}
```

## Go

```golang
func plusOne(digits []int) []int {
  for i := len(digits) - 1; i >= 0; i-- {
    if (digits[i] < 9) {
      digits[i]++
      return digits
    }
    digits[i] = 0
  }
  return append([]int{1}, digits...)
}
```

## Rust

```rust
impl Solution {
  pub fn plus_one(digits: Vec<i32>) -> Vec<i32> {
    let mut digits = digits;
    let mut i = digits.len() - 1;
    loop {
      match digits[i] {
        9 => {
          digits[i] = 0;
        },
        a => {
          digits[i] = a + 1;
          return digits;
        },
      }
      if i == 0 {
        break;
      }
      i -= 1;
    }
    digits.insert(0, 1);
    digits
  }
}
```
