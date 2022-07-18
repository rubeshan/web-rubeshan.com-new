---
draft: true
layout: post
optimized_image: https://ucarecdn.com/dae3cff1-f27a-4c09-9369-62e5d1715572/-/resize/800x600/large.png
author: Ruben
post_thumbnail: https://ucarecdn.com/dae3cff1-f27a-4c09-9369-62e5d1715572/-/resize/800x600/large.png
featured: false
date: 2021-08-01T20:33:32.833Z
title: Google Interview Question - Gas Station
subtitle: Most of the SDE may have gone through the interview and seen a similar problem.
description: Google is known for its coding interview questions. Here is one of
  the popular question which they ask in their selection process.
image: https://ucarecdn.com/dae3cff1-f27a-4c09-9369-62e5d1715572/-/resize/800x600/large.png
category: examples
tags:
  - interview
  - career
  - google
paginate: false
---

Given two integer arrays **A** and **B** of size **N**.\
There are **N** gas stations along a circular route, where the amount of gas at station **i** is **A\[i]**.

You have a car with an unlimited gas tank and it costs **B\[i]** of gas to travel from station **i**\
to its next station **`(i+1)`** You begin the journey with an empty tank at one of the gas stations.

Return the minimum starting gas station’s index if you can travel around the circuit once, otherwise return -1.

You can only travel in one direction. **`i to i+1, i+2, … n-1, 0, 1, 2..`** Completing the circuit means starting at **i** and\
ending up at **i** again.

For Example

```Input 1:
    A =  [1, 2]
    B =  [2, 1]
Output 1:
    1
    Explanation 1:
        If you start from index 0, you can fill in A[0] = 1 amount of gas. Now your tank has 1 unit of gas. But you need B[0] = 2 gas to travel to station 1. 
        If you start from index 1, you can fill in A[1] = 2 amount of gas. Now your tank has 2 units of gas. You need B[1] = 1 gas to get to station 0. So, you travel to station 0 and still have 1 unit of gas left over. You fill in A[0] = 1 unit of additional gas, making your current gas = 2. It costs you B[0] = 2 to get to station 1, which you do and complete the circuit. ```