# Problem 25

## Status: Complete

![problem-25](https://github.com/dvb2017/project-euler/blob/main/problem-25/problem-25.png)

## Methodology

`n = 2
x = 1
y = 1
z = 0
i = 0
while i < 1000:
  z = x + y
  n+=1
  i = len(str(z))
  x = y
  y = z
print(n,":",z,":",i)`

To start off I will explain what each of the initial variables represents here (this is the first five lines of code).  The 'n' represents the current length of the sequence.  I am initializing the sequence at {1, 1} with the first one represented by 'x' and the second by 'y', and starting at {1, 1} is the reason I initialized the length of the sequence as two.  The 'z' is what will represent the next number in the sequence, and 'i' represents the number of integers in the 'z' value.  

The purpose of the 'while' loop is to continue iterating through the sequence until the number of integers in the final value is 1000, at which point the loop will exit.  During each iteration of the loop, the first step is to add the 'x' and 'y' values which represent the current and previous numbers in the sequence and set 'z' equal to that sum, creating the next number in the sequence.  At this point one is added to the 'n' or index value since the current value of numbers in the sequence has gone up by one.  Next, the 'i' value is set equal to the number of integers in the 'z' value.  This is done by converting the 'z' into a string and counting the length.  Next, 'x' is set equal to 'y' and 'y' is set equal to 'z' so that the sequence can be advanced.  Once the 'i' value reaches 1000 the loop is exited and the code prints the current 'n', 'z', and 'i' values.  The 'n' value is the important one here as it represents the amount of numbers in the sequence.  

## Commentary
There isn't much to add here.  Took a slightly deeper look at the Fibonacci sequence and focused on writing fast, efficient code.  Good practice here with setting up a while loop to exit at the appropriate time.

## Answer: 4782

