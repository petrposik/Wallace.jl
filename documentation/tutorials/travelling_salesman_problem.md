# Solving the Travelling Salesman Problem using Genetic Algorithms

**Author:** [Chris Timperley](http://www.christimperley.co.uk),
**Difficulty:** Beginner,
**Duration:** 15-30 minutes.

In this tutorial, we shall use Wallace to implement a generic algorithm to
solve the travelling salesman problem, in which we wish to find the shortest
possible route through a given set of cities, which visits all cities exactly once
and return to the city at which the tour was started. The TSP is a prime example
of an NP-hard, or more specifically, NP-complete, problem that can be
effectively tackled using techniques such as genetic algorithms and ant colony
optimisation.

**This tutorial assumes:**

* A basic knowledge of [Julia](http://julialang.org/).
* You know how to create and run a basic genetic algorithm within Wallace.

**By the end of this tutorial, you will be able to:**

* Implement memetic algorithms via local search operators, incorporated using
  the linear breeder.
* Extend Wallace with a simple evaluator, tailored to the travelling salesman
  problem.
* Use Wallace to implement genetic algorithms capable of solving
  permutation-based problems, such as the travelling salesman problem.

--------------------------------------------------------------------------------

## The Problem

Could do with a short description of the problem being solved in this tutorial,
perhaps along with a diagram of the Berlin-52 map, and links to the .tsp file.

## Basic Setup
For this problem, we shall be using a standard evolutionary algorithm, with the
components listed below:

| Component           | Setting                                           |
| ------------------- | ------------------------------------------------- |
| Replacement Scheme  | Generational (without elitism)                    |
| Population          | Simple (single deme)                              |
| Representation      | Permutation                                       |
| Breeder             | Linear Breeder                                    |

### Solution Representation



## Setting up the Linear Breeder
The linear breeder is the second simplest breeder provided by Wallace; it
relaxes the constraints imposed on the type and number of genetic operators
imposed by the simple breeder, allowing the user to provide an arbitrary linear
chain of operators instead. Offspring are produced by being subjecting batches of
proto-offspring to each of these operators in sequence, until the desired number
the required number have been produced as directed.

To specify a linear breeder, one needs only to provide its definition with an
ordered list of operators, and if necessary, the stage of individual development
upon which they operate, as demonstrated below:

```
_my_breeder<breeder/linear>:
  operators:
    - type:   selection/tournament
      size:   4
      stage:  genome
    - type:   crossover/pmx
      stage:  genome
    - type:   mutation/2_opt
      stage:  genome
```

However, since we're using a simple species, which has only a single stage of
development, there is no need for us to provide the `stage` property for each
operator specification. In the event we omitted the `stage` property and our
species had more than a single stage of development, then the stage would
default to the canonical genotype.

```
_my_breeder<breeder/linear>:
  operators:
    - type: selection/tournament
      size: 4
    - type: crossover/pmx
    - type: mutation/2_opt
```

## Writing a Custom Evaluator

## Running the Algorithm

After having followed all the preceding steps, you should have an algorithm
that roughly looks similar to the one given below:

```
type: algorithm/evolutionary_algorithm

evaluator<evaluator/tsp>:
  cities: berlin52.tsp

replacement<replacement/generational>: {}

termination:
  evaluations<criterion/evaluations>: { limit: 100000 }

_my_species<species/simple>:
  representation<representation/permutation>:
    alphabet: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25
      26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49,
      50, 51, 52]

_my_breeder<breeder/linear>:
  sources:
    - type: selection/tournament
      size: 4
    - type: crossover/pmx
    - type: mutation/2_opt

population<population/simple>:
  size:     100
  breeder:  $(_my_breeder)
  species:  $(_my_species)
```

## Visualising the Results