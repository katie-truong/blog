---
layout: single
permalink: /product-of-array-except-self/
title: "Product of array except itself"
---

Given an array nums of n integers where n > 1,  return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

Example:

```
Input:  [1,2,3,4]
Output: [24,12,8,6]
```

```
Input:  [0,1,2,3]
Output: [6,0,0,0]
```

Note: Please solve it without division and in O(n).


At first glance, this problem seems to a very easy one, without the restriction in O(n) time. A very easy brute force solution with O(n^2) time complexity would be to use a nested for loop, and generate the multiplication as we iterate through the array. However, the restriction on time complexity means that the solution is not acceptable.

One thing that I usually forgot when I first started solving algo problems is, just because the solution requires O(n) time, doesn't mean we can only pass through an array *once*. In fact, we can pass through the array *multiple times*, or in other words, use multiple for loops; we just can't use a for loop within another for loop.

The intituition of this problem is, if we cannot have a nested for loop, we can pass through the array once, do some sort of calculations, then pass through the array, do more calculations, until we get the final result.

```
Input:  [1,2,3,4]

Result: [0,0,0,0]

Left:   [1, 1, 2,6]
Right:  [24,12,4,1]
Result: [24,12,8,6]
```


