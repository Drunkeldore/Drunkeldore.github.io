---
layout: default
title:  "75 Days of Leetcode - Day 7"
date:   2024-09-07 08:08:30 -0400
categories: programming leetcode 
---

# Day 7
[Product of Array Except Self.](https://leetcode.com/problems/product-of-array-except-self/description/?envType=study-plan-v2&envId=leetcode-75) Talking to my duck made it sound a lot simpler than it was. "Just ignore the value at the current index, take the product of the rest". The duck agreed. 

So something like this:

```
answer = []
nums_copy = []

for each in range(len(nums)):
    pro = 1

    for test in range(len(nums)):

        if each == test:
            continue
        pro *= nums[test]
    
    answer.append(pro)
return answer
```

It's bad, I'm bad, lets move on.

## Rules matter
**You must write an algorithm that runs in O(n) time and without using the division operation**. It works! ... kind of. So like I said, it's bad. Even if we ignore the rule the nested for loops are just too slow. 

I moved some things around, and tried to seperate the loops. I had something similar to the solution below but couldn't wrap my head around how to get the suffix array correct. 

I checked out the solutions and found this little snippet: `for i in range(n - 2, -1, -1)`. It moves through the array backwards just like I needed. Perfect!

Credit goes to [DevOgabek](https://leetcode.com/u/DevOgabek/) on LeetCode. Their code is found below: 

```
prefix = [1]
suffix = [1]

for i in range(1, n)
    prefix[i] = prefix[i - 1] * nums[i - 1]

for i in range(n - 2, -1, -1)
    suffix[i] = suffix[i + 1] * nums[i + 1]

answer = prefix[i] * suffix[i] for i in range(n)

# woo
```
## Implementing it
So I created two new arrays, prefix and suffix. Prefix is pretty simple, it loops through and multiplies the value and the previous index in nums with the value at the previous index of prefix. Effectively finding the product of every the before the current index.

The suffix does the same things but backwards. Looping from one before the last index to the start, finding the product of the values after the current index.
<div style="display:flex; align-items:center;">
<a href="" style="float:left; margin:15px;">
<img src="/assets/images/leetcode-day-7.jpg" height="280" width="720" />
</a>

I wanted to make sure I totally understood DevOgabek's solution because I was still having a hard time conceptualizing the two arrays coming together. So I whiteboarded the steps if the num array was: [1, 2, 3, 4]. Apologies for the image quality, I wanted it to match my handwriting, apparently. 

So there is day 7 of the now 9 day journey on LeetCode's 75 day challenge. 
</div>
