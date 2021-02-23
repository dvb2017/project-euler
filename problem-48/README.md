# Problem 48

## Status: Complete

![problem-X](https://github.com/dvb2017/project-euler/blob/main/problem-48/problem-48.png)

## Methodology

This question deals with what the writers call "self powers."  From my brief research, it appears that these are not a notable mathematical concept in their own right, but rather an invention for the purpose of this problem.  Beyond that, the request is very straightforward.  We are to find the sum of a series of these self powers from one to one thousand and give the last ten digits as the solution.  Since the code for this problem was very short I will include it in its entirety.  

```
y = 0
total = 0
for x in range(1,1001):
    y = x**x
    total += y
total
```

My first step here was to initialize the two variables y and total as zero.  The y value would serve as the value of each self power, and the total is simply the running total of these values.  I iterated through the range from one to one thousand, finding the aforementioned self power for each and adding it to the running total.  After iterating through every value I simply returned the final total to arrive at the answer to the problem.  

## Commentary
There is not much to add here.  Self powers themselves don't provide a very interesting topic and the technical aspect of this problem was fairly simple.

## Answer: 9110846700
