# Advent Of Code 2024

> https://adventofcode.com/2024

Solutions built using [Cyberchef](https://gchq.github.io/CyberChef/). It's neither fast nor practical, but it is fun!

## Solutions summaries

For the solutions for which I have extra inspiration, I will add some notes here.

### Day 01

Immediately a deep dive in the possibilities (or the lack thereof) of Cyberchef. Cyberchef has no obvious way to operate on columns separately. You can use `Fork` to apply operations on text split by a separator but it's not easy to combine disjoint parts into one operation. This is solved by adding a prefix to the values in a column with the column number and then sorting the input. This way we have all values of the first column first and the values of the second column after that. A split and fork lets us operate per column after this.

By adding linenumbers, and sorting everything together again we get a pairwise list of numbers that we needed to compare.

To illustrate the flow the data goes through.

```
# Example input
1 4
3 2

# Add prefix
c1_1 c2_4
c1_3 c2_2

# Sort
c1_1 c1_3 c2_2 c2_4

# Split
c1_1 c1_3
c2_2 c2_4

# Fork and add line numbers
1 c1_1
2 c1_3
1 c2_2
2 c2_4

# Combine again
1 c1_1, 1 c2_2, 2 c1_3, 2 c2_4

# Split on every set of c1, c2
c1_1, c2_2
c1_3, c2_4

# Remove prefixes
1, 2
3, 4

# Do the math
```


### Day 02

A bit easier to find a solution for the first part of day 2 compared to day 1. We start working per row by using `Fork`. Then we duplicate numbers to create pairs. We subtract them from eachother and wil use `Flow Control` operations to validate the output. We can place labels and use regexes in the `Conditional Jump` block to check if we have all positive or negative numbers and if they are 1, 2 or 3.

For the second part I could not think of a solution yet.
