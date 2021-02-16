# Problem 29

## Status: Complete

![problem-29](https://github.com/dvb2017/project-euler/blob/main/problem-29/problem-29.png)

## Methodology
```
powers_list = []
for x in range(2, 101):
    for y in range(2, 101):
        power = x**y
        powers_list.append(power)
list_set = set(powers_list)
new_list = list(list_set)
new_list.sort()
len(new_list)
```
The complete code for this problem can be seen above.  This problem was rather simple.  First, I initialized an empty list that would hold all of the power values.  Next, I created a for loop nested within another for loop, and set them both to iterate through the integers from two to one hundred.  Within the inner loop I then took the first value to the power of the second value.  Then, I added the result to the initial list.  Once that loop completed I would have a list of all the resulting values, but it would include duplicates.  In order to get rid of these duplicates I reformatted the list as a set, and then back into a list.  Finally, I found the length of that resulting list which gave me the number of unique values.  

## Commentary
Not much to say here.  This was a very simple case of using a nested loop.  One new aspect that I haven't made use of before was converting the list into a set.  This is a quick and efficient method of finding the unique values in a list.  

## Answer: 9183
