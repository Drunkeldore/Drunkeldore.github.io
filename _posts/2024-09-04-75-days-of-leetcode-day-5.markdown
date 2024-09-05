---
layout: default
title:  "75 Days of Leetcode - Day 5"
date:   2024-09-04 20:07:33 -0400
categories: programming leetcode 
---

# I started grinding leetcode
As of today I am 5 days into doing at least one leetcode problem a day. I would like to talk about my progress daily in a blog post but **cannot** hold myself to it, haha.

*also Space Marines 2 comes out tomorrow and I obviously need to play that, maybe review?*

## Today's problem
I needed to reverse a string's vowels while leaving the other words intact. My solution:
```
        vowels = ['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U']
        string_list = []
        track_dict = []
        vowel_counter = 0
        normal_counter = len(s) - 1
        for each in s:
            if each in vowels:
                track_dict += each
            string_list += each
        
        for each in string_list[::-1]:
            if each in vowels:
                string_list[normal_counter] = track_dict[vowel_counter]
                vowel_counter += 1
            normal_counter -= 1
        return "".join(string_list)
```

I added each letter to a list while also seperating out the vowels in another. I then looped back over the list, backwards, exchanging the letter, if it was a vowel, with the next letter in the list of vowels.

I believe this is O(N) time and space complexity due to the lack of nested for loops. I look forward to exploring quicker and more elegant solutions.