# Problem 41

## Status: Work-in-Progress

![problem-X](https://github.com/dvb2017/project-euler/blob/main/problem-41/problem-41.png)

## Methodology
As can be seen from the title of the problem on the Project Euler archive, this question deals with a phenomenon known as pandigital prime numbers.  This is a number which contains all of the integers from 1 to n exactly once where n is a given base and is also prime.  Zero is generally included in these numbers, but this question has specifically requested we start with one.  An example of a pandigital number under this definition would be 123, in the case that n = 3.  This is not, however, a pandigital prime because it is divisible by three.  Every combination of these three digits would be another pandigital number.  The question is simply requesting that we find the largest one of these primes that exists.  

Initially, this seems like a large undertaking.  After all, there are nearly one million pandigital numbers, so checking each one for primality would take quite some time.  This is especially true because we would be examining large numbers first, which generally take longer to check for primality.  There are a few ways that the scope of this problem can be drastically narrowed down though.  The first and most important is by simply adding up the digits.  Since all of the pandigital numbers contain the same digits in different orders, the sum of these digits will be uniform for each base.  Because this is the case, there is a handy rule in mathematics that will allow us to remove many potential options.  If the digits of a number add up to a total that is divisible by three, that number will be divisible by three.  By adding up the digits from one to nine, one to eight, and one to seven we get totals of 45, 36, and 28.  The first two are divisible by three and the latter is not.  This means that every single combination of one through nine and one through eight will be divisible by three.  Therefore, the largest possible prime will at most have a base of seven.  This removes over 725,000 potential options to iterate through from our starting point.

Once this was established, I created a list of the pandigital numbers using base seven with itertools, and sorted this list in reverse order.  At this point all that was left to do was create a loop that would check each item on this list for primality and break the loop once it found one.  I did exactly that and had my solution in just a few seconds.   

A side note I will add is that I took the time to create a prime testing function while solving this problem.  After working on a decent number of questions from Project Euler I have noticed that many of them involve finding prime numbers, since this is a fairly important topic in computer science and mathematics.  Going forward, I will be able to make use of this function whenever I'm tasked with finding primes. This should simplify many future problems and make my work much easier.   I've included the code for this function below.  
```
def is_prime(n):
    if n % 2 == 0 or n % 3 == 0:
        return False
    for i in range(5, int(n**0.5) + 1, 6):
        if n % i == 0 or n % (i + 2) == 0:
            return False
    return True
```
## Commentary
As far as commentary for this problem, there were a few interesting topics I would like to discuss.  The first of course would be pandigital numbers.  This is actually a concept I was unfamiliar with before this question.  While they do have some interesting properties, such as the sum of their digits being the same for each base, this is fairly surface level and they are more of a novelty than anything else.  The more important lesson gleaned from working on this problem was the divisible by three rule.  Even though I learned this most likely in grade school it has been about that long since I used it as well.  It was incredibly useful in this problem however, and forcing myself to think about this property of mathematics has made me reconsider its utility in solving other problems as well.   I tend to think about the overall value of numbers when I'm working with them, so taking a moment to examine the digits and their significance served as a valuable step back.  

## Answer: 7652413
