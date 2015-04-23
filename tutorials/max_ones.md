# Max Ones
### An Introduction to Solving Optimisation Problems with Genetic Algorithms

**Author:** [Chris Timperley](http://www.christimperley.co.uk),
**Difficulty:** Beginner,
**Duration:** 10-30 minutes.

In this tutorial, we will be using Wallace to implement a simple Genetic
Algorithm to solve the benchmark Max Ones optimisation problem, where we attempt
to maximise the number of 1s in a fixed-length bit-string. This problem is
trivial for humans, of course, but is slightly less so for "blind" evolutionary
algorithms.

Outline of this tutorial.

**This tutorial assumes:**
* A minimal knowledge of [Julia](http://julialang.org/).
* You know how to navigate the Julia REPL when using Wallace.
* You know how to load Wallace specification files and run them.
* You know a little bit about the basic structure of Wallace specification files. 

**By the end of this tutorial, you will be able to:**
* Write a simple binary-string genetic algorithm.
* Use Wallace to solve simple binary-string optimisation problems, such as the
  Max Ones problem.

--------------------------------------------------------------------------------

## Getting Started

> **Question:** *Does the fitness of the best individual in the population
  always improve or stay the same?*

-------------------------------------------------------------------------------

## Troubleshooting