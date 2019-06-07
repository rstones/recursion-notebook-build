---
interact_link: content/recursion.ipynb
kernel_name: python3
has_widgets: false
title: 'Recursion'
prev_page:
  url: 
  title: ''
next_page:
  url: 
  title: ''
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# Recursion

    def. see Recursion
    
Or more succinctly...recursion is a way of defining something in terms of itself or its type!

In computing, we can perform certain calculations by breaking them down into self-similar pieces. We will see later in this lesson how functions can be called from within themselves to elegantly construct solutions to problems. You will get some practice with writing recursive functions and we will also discuss in which situations recursion might be useful for dealing with certain types of data.

<img crossorigin="anonymous" src="https://upload.wikimedia.org/wikipedia/commons/f/fd/Von_Koch_curve.gif" class="mw-mmv-final-image gif mw-mmv-dialog-is-open" alt="">



### Exercise 1



We are going to warm up by writing a function to calculate the factorial of a non-negative integer $n$ using a for-loop.

The factorial of $n$ is defined:

$ n! = n\times(n-1)\times(n-2)\times...\times2\times1$

Writing out the maths explicitly for some small numbers should give you an idea of how the factorial is calculated...

$0! = 1$ (this is a special case)

$1! = 1$

$2! = 2\times1 = 2$

$3! = 3\times2\times1 = 6$

$4! = 4\times3\times2\times1 = 24$

$5! = 5\times4\times3\times2\times1 = 120$

and so on...

In the cell below complete the function to calculate the factorial using a for-loop.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# calculate factorial of a non-negative integer n using a for loop
def factorial_loop(n):
    pass

```
</div>

</div>



Now try out your new function by testing it against some values given for the factorial above. If it doesn't work can you work out why? Don't forget to test the special case 0!



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# try out your function here
factorial_loop(0)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
1
```


</div>
</div>
</div>



### Exercise 2



The factorial can also be expressed in terms of another factorial, ie. recursively!

$n! = n\times(n-1)!$

$n! = n\times(n-1)\times(n-2)!$

$n! = n\times(n-1)\times(n-2)\times(n-3)!$

and so on until...

$ n! = n\times(n-1)\times(n-2)\times...\times2\times1$

which is the definition we saw earlier.

So rather than writing a for-loop to calculate the factorial of $n$ like we did before, we could multiply $n$ by $(n-1)!$. Then instead of calculating $(n-1)!$ with a for-loop we could multiply $(n-1)$ by $(n-2)!$. We could continue in this way until we reach $0!$ where we would stop.

To get you started, I will walk you through this exercise showing you the basic features of a recursive function...



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# calculate factorial of a non-negative integer n using recursion
def factorial_rec(n):
    pass

```
</div>

</div>



Now try out your new function by testing it against the one you wrote using a for-loop. Does it give the same answers even for large values of n?

Note: python will prevent you using n larger than about 1000 with a recursive function.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# try out your function here
factorial_rec(5)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
120
```


</div>
</div>
</div>



### Recursion recap



So far we have compared the use of loops and recursion to solve the same problem. In fact loops can be expressed using recursion in lots of cases. Whether recursion is the best solution will depend on the particular situation.

Two important things to remember about writing a recusive function:
- Define a base case which will stop the recursion
- Call the function from within itself for a 'simplified' case of the problem



### When is recursion useful then?



When writing code, you should be aiming for a balance of readablility and performance. A general rule of thumb is to write readable code first, then optimise if you need to.

Recusion might be the most natural way to express a problem (instead of using a loop say) but it can sometimes affect performance. Calling a function from within itself many times can take up a lot of memory or take longer to run compared to a loop.

Cases where recursion seems particularly natural for expressing a solution are when using nested data structures such as lists of lists and dictionaries of dictionaries:

```python
nested_list = [1, [2,3,4], [5,6,[7,8,9]] # a list containing more lists

nested_dict = { # a dictionary containing more dictionaries
    'a': {
        'c': {
            'd': 'some data'
        }
    },
    'b': {
        'e': 'more data'
    }
}
```



### Exercise 3



For the final challenge we are going to write out the lyrics for the Twelve Days of Christmas using recursion!

Below are lists of the gifts and the days...



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
gifts = [
    'a partridge in a pear tree',
    'two turtle doves',
    'three French hens',
    'four calling birds',
    'fiiiive goooold riiiiings',
    'six geese a-laying',
    'seven swans a-swimming',
    'eight maids a-milking',
    'nine ladies dancing',
    'ten lords a-leaping',
    'eleven pipers piping',
    'twelve drummers drumming'
]

days = [
    'first',
    'second',
    'third',
    'fourth',
    'fifth',
    'sixth',
    'seventh',
    'eighth',
    'nineth',
    'tenth',
    'eleventh',
    'twelveth'
]

```
</div>

</div>



There are three functions that we will need.

The function ```verse_gifts(day)``` returns the list of gifts at the end of a verse on the given day.  Eg. on the third day 'three French hens, two turtle doves and a partridge in a pear tree'.

This is an example of a recursive function with a base case (day 1) and recursive function call appending a list of gifts from the previous day to the gift received on the current day.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# construct a string of all the gifts received on a given day
def verse_gifts(day):
    if day == 1:
        # base case, return the gift from the first day
        return gifts[0]
    else:
        # recursively get the gifts from the current day and all previous days
        # we need to use a conditional expression on day 2 to add the 'and'
        return gifts[day-1] + ',\n' + ('and ' if day == 2 else '') + verse_gifts(day-1)

# print the gifts recieved in a verse
print(verse_gifts(3))

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
three French hens,
two turtle doves,
and a partridge in a pear tree
```
</div>
</div>
</div>



The function ```verse(day)``` constructs the string for a single verse calling ```verse_gifts(day)``` to get the list of gifts sent on that day.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# construct a verse for a given day
def verse(day):
    return 'On the ' + days[day-1] + ' day of Christmas my true love sent to me,\n' + verse_gifts(day) + '.\n\n'

# print a verse
print(verse(3))

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
On the third day of Christmas my true love sent to me,
three French hens,
two turtle doves,
and a partridge in a pear tree.


```
</div>
</div>
</div>



The function ```song(day)``` returns all the verses up to a given day. So if we call song(5) we should get a string containing all the verses up to day 5.

We could do this using a loop but lets try completing this function using recursion.

Then print the lyrics to whole song :-)



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# construct the whole song up to the verse for a given day
def song(day):
    pass

# print the whole song
print(song(12))

```
</div>

</div>

