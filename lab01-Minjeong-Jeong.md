Lab 01
================
Minjeong Jeong
2018년 1월 28일

For instance, consider the monthly bills of Leia (a stats undergrad student): cell phone $80, transportation $20, groceries $527, gym $10, rent $1500, other $83. You can use R to find Leia's total expenses:

``` r
# total expenses
80 + 20 + 527 + 10 + 1500 + 83
```

    ## [1] 2220

For example, you can create an object `phone` for the cell phone bill, and then inspect the object by typing its name:

``` r
phone <- 80
phone
```

    ## [1] 80

Make more assignments to create variables `transportation`, `groceries`, `gym`, `rent`, and `other` with their corresponding amounts:

``` r
transportation <-20
 groceries <-527
 gym <-10
 rent <-1500
 other <-83
```

Now that you have all the variables, create a `total` object with the sum of the expenses:

``` r
# total expenses
groceries+gym+other+phone+rent+transportation
```

    ## [1] 2220

Assuming that Leia has the same expenses every month, how much would she spend during a school "semester"? (assume the semester involves five months)

``` r
# semester expenses
2220*5
```

    ## [1] 11100

Maintaining the same assumption about the monthly expenses, how much would Leia spend during a school "year"? (assume the academic year is 10 months)

``` r
# year expenses
2220*10
```

    ## [1] 22200

R has many functions. To use a function type its name followed by parenthesis. Inside the parenthesis you pass an input. Most functions will produce some type of output:

``` r
# absolute value
abs(10)
```

    ## [1] 10

``` r
abs(-4)
```

    ## [1] 4

``` r
# square root
sqrt(9)
```

    ## [1] 3

``` r
# natural logarithm
log(2)
```

    ## [1] 0.6931472

``` r
# this is a comment
# this is another comment
2 * 9
```

    ## [1] 18

``` r
4 + 5  # you can place comments like this
```

    ## [1] 9

``` r
# case sensitive
phone <- 80
Phone <- -80
PHONE <- 8000

phone + Phone
```

    ## [1] 0

``` r
PHONE - phone
```

    ## [1] 7920

``` r
# your vector expenses
expenses<-c(phone,transportation,groceries,gym,rent,other)
```

``` r
barplot(expenses)
```

![](LAB1_files/figure-markdown_github/unnamed-chunk-12-1.png)

``` r
sort(expenses, decreasing=FALSE)
```

    ## [1]   10   20   80   83  527 1500

``` r
names(expenses)=c("phone","transportation","groceries","gym","rent","other")
barplot(sort(expenses,decreasing=FALSE ))
```

![](LAB1_files/figure-markdown_github/unnamed-chunk-14-1.png)

Calculate the hypotenuse of a right triangle with legs of length 3 and 4. Use the `sqrt()` function, and create variables `a = 3` and `b = 4`. If you don't know what's the symbol to calculate exponents, search for the help documentation of the arithmetic operators: `?Arithmetic`.

``` r
?Arithmetic
```

    ## starting httpd help server ... done

``` r
a<-3
b<-4
```

``` r
a^2+b^2
```

    ## [1] 25

``` r
# where:
#- $n$ is the number of (fixed) trials
#- $p$ is the probability of success on each trial
#- $1 - p$ is the probability of failure on each trial
#- $k$ is a variable that represents the number of successes out of $n$ trials
#- the first term in parenthesis is not a fraction, it is the number of combinations in which $k$ success can occur in $n$ trials

#For instance, the number of combinations in which $k$ = 2 
#success can occur in $n$ = 5 trials is:

choose(n = 5, k = 2)
```

    ## [1] 10

``` r
#Conveniently, R also provides the function `factorial()` to calculate the factorial of an integer:

factorial(4)
```

    ## [1] 24

``` r
#Let's consider a simple example. A fair coin is tossed 5 times. What is the probability of getting exactly 2 heads?

n<-5
k<-2
p<-0.5
```

``` r
# Use `factorial()` to compute the number of combinations "_n choose k_"
# Apply the binomial formula, using `factorial()`, to calculate the probability of getting exactly 2 heads out of 5 tosses.

(factorial(n)/(factorial(n-k)*factorial(k)))*p^k*(1-p)^(n-k)
```

    ## [1] 0.3125

``` r
#Recalculate the same probability but now using `choose()` (instead of `factorial()`)
choose(n = 5 , k = 2)*p^2*(1-p)^3
```

    ## [1] 0.3125

``` r
#Consider rolling a fair die 10 times. What is the probability of getting exactly 3 sixes?
(factorial(10)/(factorial(7)*factorial(3)))*p^3*(1-p)^7
```

    ## [1] 0.1171875

Now look for help documentation (e.g. `help.search()` or `??`) using the keyword binomial: `binomial`.

``` r
? binomial
```

-   You should get a list of topics related with the searched term `binomial`.
-   Choose the one related with the *Binomial Distribution*, which is part of the R package `stats` (i.e. `stats::Binomial`).

``` r
#Read the documentation and figure out how to use the `dbinom()` function to obtain the above probabilities: 2 heads in 5 coin tosses, and 3 sixes in 3 rolls of a die.
probability<- 0.5
head<- 2
flip<- 5
sixes<- 3
Probofdie<- 1/6
roll<- 3
```

``` r
#probabilities: 2 heads in 5 coin tosses
dbinom(head,flip,probability)
```

    ## [1] 0.3125

``` r
#probabilities: 3 sixes in 3 rolls of a die
dbinom(sixes,roll,Probofdie)
```

    ## [1] 0.00462963

``` r
#How would you modify the previous binomial function to calculate the same probability (2 heads in 5 tosses) of a __biased__ coin with a chance of heads of 35%?
probability<-0.35
dbinom(head,flip,probability)
```

    ## [1] 0.3364156

``` r
#Finally, obtain the probability of getting more than 3 heads in 5 tosses with a biased coin of 35% chance of heads.
dbinom(0:3,flip,probability) #probability of getting between 0 and 3 heads
```

    ## [1] 0.1160291 0.3123859 0.3364156 0.1811469

``` r
sum(dbinom(0:3,flip,probability)) #probability of less than 4 heads in 5
```

    ## [1] 0.9459775

``` r
1-sum(dbinom(0:3,flip,probability)) #probability of more than 3 heads in 5 tosses
```

    ## [1] 0.0540225

Install packages `"stringr"`, `"RColorBrewer"`, and "`XML`"
===========================================================

install.packages(c("stringr","RColorBrewer","XML"))

``` r
#Calculate: $3x^2 + 4x + 8$ when $x = 2$
x<-2
3*x^2+4*x+8
```

    ## [1] 28

``` r
#Calculate: $3x^2 + 4x + 8$ but now with a numeric sequence for $x$ 
x <- -3:3
3*x^2+4*x+8
```

    ## [1] 23 12  7  8 15 28 47

``` r
#Find out how to look for information about math binary operators like `+` or `^` (without using `?Arithmetic`).
#There are several tabs in the pane `Files, Plots, Packages, Help, Viewer`.
#Find what does the tab __Files__ is good for?
#What about the tab __Help__? 
# Help: providing all information about syntax
#In the tab __Help__, what happens when you click the button with a House icon?
#It shows us resources, manuals, studio
#Now go to the tab __History__. What is it good for? and what about the buttons of its associated menu bar? It show all the syntax I put 
#Likewise, what can you say about the tab __Environment__? showing all variables
```

example 1
=========

var&lt;- 3 Var\*2 \# Error! Case sensitivty

example 2
=========

x&lt;-2 2x&lt;-2\*x \# The name of variable can't start with number

example 3
=========

sqrt4 &lt;- sqrt(4) sqrt4 \# It is 2

example 4
=========

a number &lt;- 16 \#Error NO space in the name of variables

example 5
=========

"one number" &lt;- 16 `one number` one number \#Error put " "
