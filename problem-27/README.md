# Problem 27

## Status: Complete

![problem-27](https://github.com/dvb2017/project-euler/blob/main/problem-27/problem-27.png)

## Methodology
```
prime_list = [2]
my_val = 3
while my_val < 1000:
    for x in range(2,my_val):
        my_check = my_val % x
        if my_check == 0:
            break
        elif x + 1 == my_val:
            prime_list.append(my_val)
            print(my_val)
            break
    my_val += 1 
a = -79
b = prime_list
```
I won't be including the full code in this description since it was fairly long.  That can still be found in the Jupyter notebook file as usual.  What I have included above is the method I used to initialize the `a` and `b` values, as this was the most important part of solving this problem.  To start, I have initialized a list containing only the number two.  I will be appending this list with all of the prime numbers under one thousand.  I've included the integer two on the initial list to simplify my code as it is slightly easier to calculate prime numbers if two is assumed rather than creating an if-else exception.  The while loop here then iterates through all of the numbers one to one thousand.  For each of these numbers it finds if it is prime by checking the modulo value for every lower number.  If none of these evaluate to zero (meaning that the number is divisible by that other number making it composite), it is added to the list of primes.  The reason that I have done this is because `b` must be a prime number one and one thousand.  The easiest way to support this assumption is to test the case where zero is run through the equation.  In this case the first two terms are zeroed out and only the `b` term remains.  If this is not a prime number then none of the following cases matter since the first case (zero) must evaluate to prime.  

The `a` term has been initialized as -79 above.  This is simply because the example given in the problem had that value for `a` while the `b` value was larger than the one thousand cap imposed by the question.  These two terms are meant to offset each other when the `a` is negative, so if `a=79` requires `b=1601` to offset it, the amount that a `b` value under one thousand can offset will necessariily be lower.  So in order to cut down on computation time we can set 79 as the cap on the `a` value rather than the minimum of negative one thousand offered by the problem.

From here the problem is reltively straightforward.  I have structured it as a for loop within a for loop within a while loop.  The two outer loops simply cycle through the potential values for `a` and `b`.  The inner for loop is where the heavy lifting is done.  Here, the value of the quadratic equation is calculated given the `a` and `b` values and starting with an `n` value of zero.  This value is then checked for primality using a similar method as when the list of primes was calculated for the `b` values.  If the first case is prime, one "point" is added to a counter and also to the `n` value.  Then the next value for the equation is calculated using that new `n` value and it is once again checked for primality.  This repeats until the equation evaluates to a composite number, at which point a number of actions take place.  First, the inner loop is exited.  Next, the counter that keeps track of how many consecutive primes have been found is compared to a value named `high_prime` which tracks the longest streak.  If the current streak is longer than the historic record it replaces it, and the `a` and `b` values used to attain that record are recorded as well.  The `n` value is reset to zero at this point, and the `b` value changes to the next prime on the list.  Once every `b` value has been tested for a given `a` input, the `a` is increased by one.  Once the loops are completed every possible combination of these two inputs will have been tested, and the remaining `high_prime` value will be the longest overall streak as the problem requested.  The two factors that resulted in this streak will have also been saved and can be multiplied together to find the solution.

## Commentary
There were a few aspects of this problem that gave me food for thought.  The first was input selection.  The initial problem requested that absolute values of each term should be less than or equal to one thousand.  So the range for both `a` and `b` was -1000 to 1000.  This gives us a range containing roughly 2000 numbers for each variable.  There would be four million different combinations of these variables.  Narrowing these ranges down to -79 to 79 and the 168 primes under one thousand resulted in a much more manageable 26544 possible combinations.  This meant using a fraction of the computation time (less than one one-hundredth).  The other useful tool that I picked up while working on this problem was using the `break` statement.  Until this point I have always used workarounds to exit loops and simply wait for a for loop to run its course.  Not wanting to waste computation time here though, I found that implementing this statement after the first composite was found in a sequence to immediately move on to the next value sped up my code considerably.   

## Answer: -59231
