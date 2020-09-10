# A quick primer on Cyclomatic complexity

Cyclomatic complexity(CC) is the measure of how many 'cycles' it takes to hit every path of an application

CC is expressed as a value X. An application will have a certain value for X based on its featureset. If we reduced the value of X, we wouldn't have the same application anymore, it would have fundamentally changed.

What we can do, however, is group the complexity into things like functions, classes and modules and lower the average complexity **per group**

The two main benefits of CC are that the code will be easier to read and easier to test. Furthermore, when a change is needed to one of the groups, it is easier to make those changes on a group with low CC. This increases confidence in making those changes, which means you can make them faster!

> Many functions, classes, modules with low complexity is often (but not always) easier to manage
>
> -- <cite>Kyle Shevlin</cite>

### Sources

[Managing Cyclomatic Complexity](https://kyleshevlin.com/managing-cyclomatic-complexity)
