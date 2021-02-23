# Problem 187

## Status: Complete

![problem-187](https://github.com/dvb2017/project-euler/blob/main/problem-187/problem-187.png)

## Methodology
The methodology for this problem was very straightforward.  As can be seen above, the goal was to find the number of semi primes (composite numbers with exactly two prime factors) under one hundred million.  While this is simple, it does present an obvious problem.  The easiest way to find semi primes is by first finding prime numbers and multiplying them to arrive at the semi primes.  And therein lies the issue.  Calculating prime numbers takes a large amount of computation power, especially when the numbers are large.  Luckily, there are ways to narrow this down a bit so that the program doesn't take too long to run.  The most important step I took was to search numbers under fifty million for primes rather than under one hundred million.  This is because fifty million times two, the smallest prime number, is one hundred million.  Any primes higher than fifty million will not be able to be multiplied by any other prime number and remain under the target of one hundred million. 

Once I had compiled a list of prime numbers under fifty million, the next task was to multiply them all by each other and create a list of the products that were under one hundred million.  I did this by using a nested for loop that with a variable iterating through the prime number list on the inner and outer loop.  Both started at two and when the inner loop reached a product greater than one hundred million it was exited since any further products would also be too large.  This left me with a list of the semi prime products, although it did contain duplicates.  To remedy this I converted the list into a set and then back into a list.  What remained was a list of the unique semi primes under one hundred million.  To arrive at the solution I simply found the length of the list.  

## Commentary
There is not much to add here.  Semi prime numbers are not particularly interesting to me, and I found it easier to calculate the primes first rather than factor each number under one hundred million.  I believe this was the faster method since the time cost increased exponentially as larger numbers were checked.  

## Answer: 17427258
