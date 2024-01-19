# The BIN PACKING Problem

The bin packing problem can be defined as follows:

> Given a set of items of varying sizes, what is the smallest number of containers of a given size needed to contain those items?

For example, imagine we have two items of size 1 and size 4, and we need to fit these objects into a minimum number of containers of size 10. In this case the solution is that we need just one container with both items packed inside it.

Things obviously get more interesting when we have a lot of items. If we have 10 000 objects ranging in size from 1-10, how many size-10 containers do we need to pack those objects optimally?

Despite its relatively simple formulation the bin packing problem is a classic of computer science, with continuing attempts to find more and more optimal solutions. It is also not just an abstract problem, it has real-world application in a number of areas, for example:

1. Storing chunks of data in memory efficiently
2. Organising task queues for optimal performance
3. Fitting your favourite tunes onto a mix tape

## Your Challenge

Implement a bin packing algorithm using Test Driven Development: 

1. Write a test for your algorithm that fails - RED
2. Make the test pass - GREEN
3. Make the code better - REFACTOR
4. Write a new failing test and repeat

Your first failing test has been written for you.

The index signature for the `binPack` function has been created for you:

```ts
export const binPack: (input: number[]) => number[][]
```

In other words, this is a function that takes an array of numbers and returns an array of arrays representing those numbers packed into bins of a given size.

For example, for the trivial case above:

```ts
binPack([1, 4]) = [[1, 4]];
```

For a more complicated case:

```ts
binPack([4, 7, 2, 8]) = [[4], [7, 2], [8]]; // Note this is only one possible answer, it is not necessarily the best answer
```

## Approaches

There are a few naive approaches to the bin packing problem that you might try (together with lots of more complicated solutions on the other end of a google search):

1. Next Fit - check if the current item fits in the current bin. If it fits, put it in that bin, otherwise put it in a new bin.

2. First Fit - iterate through all bins and check each one in turn to see if your object will fit. If you cannot find a bin to put it in, create a new bin in which to store it.

3. Best Fit - scan your current bins and find the one where the fit is tightest (i.e. it fits in with the least amount of remaining space). If no match is found, create a new bin to store it.

4. First Fit Decreasing - same as First Fit but you first order your objects by size from largest to smallest.

5. Best Fit Decreasing - same as Best Fit but again you first order your items by size from largest to smallest.

> TIP: Bear in mind that for some of these implementations you are likely to need to create subsidiary functions - for example `objectFitsInBin` or `getTightestFittingBin` for which you will likely want to create tests as well.

## Acceptance criteria

1. Objects are limited to a size of between 1 and 10 (you might consider your function throwing an error if this is not satisfied);
2. Containers are size 10 (you might consider allowing this to be set in a later optimisation, but stick to 10 in the first instance);
3. The output should be a two-dimensional array representing the items sorted into bins;

## Test Cases

1. Trivial result: 

```ts
binPack([n]) = [[n]]; // for all n in range 1...10
```

2. Set of objects that fit in one bin:

```ts
binPack([m, n, o]) = [[m, n, o]];
```

3. General case:

```ts
binPack([m, n, ....]) // =?;
```

4. Error handling?