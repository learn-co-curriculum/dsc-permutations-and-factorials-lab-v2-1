# Permutations and Factorials - Lab

## Introduction

Before, we saw how the creation of a sample space is crucial in finding probabilities. The issue, however is that, when the sample space grows bigger, it is not straightforward to manually compute the size of sample sets anymore.

Luckily, probability theory provides us with several formulas that can help us out. One set of formulas is known as **permutations**. This lab will help you get a better understanding of permutations, and provide practice!

## Objectives

You will be able to:

* Mathematically derive how many permutations there are for large sets
* Calculate permutations of a subset
* Calculate permutations with repetition and replacement

## A Note on Factorials

In the last lesson, we talked about permutations in the context of a coverband creating a setlist. We wanted to calculate how many ways we can order 3 songs in their setlist. We can use factorials for that. For 3 songs, this boils down to


```python
setlist = 3*2*1
```

Now, writing this out is not an issue when $n$ is small. What if $n$ grows though? Imagine there are 10 songs in the setlist


```python
setlist = 10*9*8*7*6*5*4*3*2*1
```

You wouldn't want to repeat this for 25 songs...  Let's create a function for this!

What you'll do below is:

- create a function that takes one argument, $n$
- initialize `prod` as 1
- next, use `prod` in a `while` loop (what is the stopping criterion?)
- update $n$ so it decreases with value 1 each iteration. This way you essentially calculate $n*(n-1)*(n-2)*\ldots*(1)$


```python
def factorial(n):
    None
```

Now, test your function with n=20


```python
None
```

Just so you know, Python has a built-in function `factorial` in the  `math` library as well! Let's use our own function in this lab, but just use the `math` function once to check your previous answer!


```python
import math 

None
```

## Some Practice on Permutations

Let's go back to the appointments exercise from the last lab. A teaching assistant is holding office hours so students can make appointments. She has 6 appointments scheduled today, 3 by male students and 3 by female students. How many ways are there to order the appointments, based on gender of the students? Just to clarify, we're looking for size of the sample space that lists possible orders like this:

FMFMFM <br />
MMMFFF <br />
FMFMMF <br />
...


From what you learned in the permutations lecture, you now have a more structured way of getting to the whole sample space! 

Hint: a permutation with repetition is needed here, with formula $\dfrac{n!}{n_1!n_2!\ldots n_k!}$. Think carefully of what needs to go in the denominator and the numerator respectively. 


```python
app_num = None
app_num
```


```python
app_denom = None
app_denom
```


```python
app_total = None
app_total
```

## Permutations: Hack a Phone

You misplaced your iPhone and are afraid it was stolen. Luckily, your iPhone needs a 4-digit code in order to get in. Imagine that a potential thief can do five attempts at getting the code right before the phone is permanently locked, how big is the chance the thief unlocks the phone?

Think about the sample space and the event space separately. You'll use the formula $P(E) = \dfrac{|E|}{|S|}$ here.

So what should go in the denominator?


```python
denom_phone = None
denom_phone
```

And the numerator?


```python
numer_phone = None
numer_phone
```


```python
prob_unlock = None
prob_unlock
```

Right before you lost your phone you ate a pretzel, and you are pretty sure a grease pattern was left on the four crucial digits of your screen. The four letters in your access code are 3,4,7 and 8, and you realize that this information can increase the thief's chances massively. Assuming the thief interprets the smudgemarks in an intelligent way, what are the chances that the phone will be unlocked successfully?


```python
denom_phone_smudge = None 
denom_phone_smudge
```


```python
numer_phone_smudge = None
numer_phone_smudge
```


```python
prob_unlock_smudge = None
prob_unlock_smudge
```

Now, imagine you chose an iphone access code containing 3 different numbers, with numbers 2,7 and 8 (the code is still 4 digits). Now, the thief knows 1 number was reused (permutations with repetition!), but he doesn't know which one. what is the probability now that the phone will be unlocked successfully?

- For the denominator here, use a permutation with repetition, along with the fact that **you don't know which one is repeated**. Hint: you'll have to multiply your final "permutation with repetition"-result to account for that.
- For the numerator, use the numerator you used before: the number of trials the thief can try before the phone access is blocked.



```python
denom_phone_smudge_2 = None
denom_phone_smudge_2
```


```python
numer_phone_smudge_2 = None 
numer_phone_smudge_2
```


```python
prob_unlock_smudge_2 = None
prob_unlock_smudge_2
```

## Permutations to Find the Sample and Event Space

What are the odds of throwing a "full house" when throwing 5 dice?  Recall, a full house means that you'd throw a three of a certain number along with a pair of a different number.

###  a) Sample space

First, calculate the sample space. Recall that replacement is possible here.


```python
sample_space_fh = None
sample_space_fh
```

### b) Event space

Next, calculate the event space. The best way to think of the event space here is to split it up in 2 parts:
- first, try to constrain your problem to a more specific problem, let's say, how many ways can we throw a full house if we have a pair of 4s and three 6s?
- next, extend your problem by asking yourself how many *different* full houses are possible.
- multiply the two!


```python
ways_to_throw_given_fh= None # permutation with repetitions
ways_to_throw_given_fh
```


```python
diff_fhses = None
diff_fhses
```

Then the event space is


```python
event_space_fh =  None
event_space_fh
```

### c) Probability of full house


```python
prob_fh = None

prob_fh
```

## Level-Up: Factorials and Recursion 

Let's return to factorials for a moment. In the last lesson, we talked about permutations in the context of a coverband creating a setlist. We wanted to know how many ways we could order 3 songs in their setlist. There were 3 possible ways of choosing a first song, 2 possible ways of choosing a second song, and only 1 way of choosing a third and final song, for $3 * 2 *1 = 6$ different ways in which the three different songs could be played. This number, 6, is equal to the factorial of 3, $3!$, the number of permutations of 3 distinct objects. 

Here, $3! = (3 * 2 * 1) = 6$. Notice that this is the same as writing $3 * 2! = 3 * (2 * 1)$ and $3 * 2 * 1! = 3 * 2 * (1)$. (By definition, the factorial of 1, $1!$, is equal to 1. The factorial of 0, $0!$ is also defined to be equal to 1.)

We can generalize this to the case of computing the factorial of an integer n, $n!$. The factorial of n, $n!$, can be written as $n * (n-1)!$, which itself can be written as $n * (n-1) * (n-2)!$. That is, we can define the factorial of n in terms of the product of n by the factorial of (n-1), and so on and so forth, as seen in the equation below: 

$$ n! = n * (n-1)! = n * (n-1) * (n-2)! = ... = n * (n-1) * (n-2) * \ldots * 1! = n* (n-1) * (n-2) * \ldots * 2 * 1 $$ 

Earlier in this lab, we defined a Python function, `factorial(n)`, to compute the factorial of an integer n. In that case, we used a `while` loop with a stopping criterion to obtain a result. 

However, there is another way we could have defined this function, using the __recursive__ nature of the factorial function.

### Recursion 
When we define a function in terms of itself, in this case, the factorial of n in terms of the factorial of (n-1), we are using **recursion**.  Recursive functions are functions that can call themselves in order to loop until a condition is met. 

We can use recursion to define a function that will return the factorial of an integer n as follows: 

``` python
def factorial_recursion(n):
    if n == 1:
        return 1
    else:
        return n * factorial_recursion(n-1) 
```

Let's go over what happens with this function for the case n = 3: 

* To start, since n is not equal to 1, we skip the `if` statement and continue to the `else` statement, where we obtain that `factorial_recursion(3) = 3 * factorial_recursion(2)`.

* To calculate `factorial_recursion(2)`, since the argument passed to the function is not equal to 1, we once again skip the `if` statement and continue to the `else` statement, where we obtain that `factorial_recursion(2) = 2 * factorial_recursion(1)`. 
    * At this point, `factorial_recursion(3) = 3 * (2 * factorial_recursion(1))`

* To calculate `factorial_recursion(1)`, since the argument passed to the function _is_ equal to 1, we return 1. 
    * At this point, `factorial_recursion(3) = 3 * 2 * 1`, and our code returns the answer we expect, `6`. 

Try it out in the code cell below!


```python
# Uncomment the lines of code below:

# def factorial_recursion(n):
#     if n == 1:
#         return 1
#     else:
#         return n * factorial(n-1) 

# factorial_recursion(3)
```

As a last step, check that the result you obtain with the `factorial_recursion` function for n = 3 is the same as the result you obtain with the `factorial` function defined earlier in this lab:


```python
# Your code here 
```

Good job! 

## Summary

In this lab, you got quite some practice with permutations and factorials, and were even able to use it to calculate probability. You also had a gentle introduction to recursive functions in Python. You'll have a chance to learn much more about recursion in Python and solve some problems using recursion in the Appendix to this Module. 

Now, we'll move over to another concept in combinatorics: combinations.
