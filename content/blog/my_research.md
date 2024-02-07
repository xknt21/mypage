---
title: "About my research in high school"
summary: "Research motivation and summary"
description: "Research motivation and summary"
date: 2024-02-07T11:26:23+09:00
author: "Kanato Nishiura"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
hideSummary: false
ShowReadingTime: true
ShowPostNavLinks: true
---

I did a research project in my high school on the topic of ["Creating a class schedule with a more constant daily load using a genetic algorithm"](https://www.ipsj.or.jp/event/taikai/85/85PosterSession/ipsj_poster/pdf/8003.pdf). Today, I would like to explain the motivation for this study and give a brief overview.

## Research motivation

Our high school's current class schedule was unsatisfactory because the load for students was unevenly distributed from day to day, such as very heavy textbooks to bring to school on one day, a very large number of assignments, and a lot of classroom movement.

However, there are so many combinations of class schedule that it is difficult to examine them all, so I used a genetic algorithm that can  derive some practical solutions in a short time.

* genetic algorithm
  *  A method for solving both constrained and unconstrained optimization problems that is based on natural selection, the process that drives biological evolution.

## Research summary

### 1. Define each subject load

The five items of "weight of luggage," "travel time," "amount of work," "physical strength," and "mental strength" were used as the load and rated on a 4-point scale from 0 to 3.   
The accuracy of the figures here is not the main theme, so we evaluated them ourselves.

### 2. Programs using genetic algorithms in Python

* Program Details
  * Create k number of random class schedules　(This is the first generation)

  * Take the standard deviation for the sum of the loads for each day of the week　(This is the evaluation value for that class schedule)

  * Apply genetic algorithm

### 3. Comparison with class schedule used in high school

The class schedule used in the high school has an evaluation value of 5.97.

However, after applying the genetic algorithm for 500 generations with 20 individuals and 5 elites, the evaluation value was 0.45.


[Click here for the code](https://github.com/xknt21/ga_timetable.git)

### Thoughts

This research was first project for me.  
There were many things that did not go well, but we were able to proceed with the advice of those around us.　　
I would like to use the perseverance and problem-solving skills I gained from this experience in my next research project.　　

Thanks for reading this far!　　
See you in the next post!