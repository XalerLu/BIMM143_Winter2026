# BIMM 143 Class 06
Xaler Lu (A17388454)

## Background

All functions in R have at least three things:  
- A **name** that we use to call the function  
- One or more input **arguments**  
- The **body** the lines of R code that do the work  
`function(arg1,arg2) { paste(body1,body2) }`  

# The Add Function

Let’s write a function called `add()` to sum up some numbers

``` r
add <- function(x, y) {
  x + y
}
```

Now we can use this function

``` r
add(100,1)
```

    [1] 101

``` r
add(c(100,1,100), 1)
```

    [1] 101   2 101

``` r
add( x=10, y=10)
```

    [1] 20

> Q. What happens when we give a multiple element vector to both `x` and
> `y`?  

``` r
add(c(100,1,100), c(100,1,100))
```

    [1] 200   2 200

> Q. What if I give three inputs to the functions like `z`?  

``` r
# add(c(100,1), 1, 1)
```

> Q. What if I give one input to the function instead?

``` r
# add(c(100,1))
```

Let’s make a new `add()` function that overrides `y`

``` r
addnew <- function(x, y=1) {
  x + y
}

addnew(c(100,1))
```

    [1] 101   2

If we write our function with input arguments having no default value,
then the user will be required to set them when they use the function.
We can give our input argument default values by setting them equal to
some sensible value - e.g. `y=1` in the `addnew()` function

## The Sequence Generating Function

The `sample()` function can be a useful starting point

``` r
sample(1:10, size=4)
```

    [1]  7  6  1 10

> Q. Can I generate nine random numbers taken from the input vector
> x=1:10?

``` r
sample(1:10, size=9)
```

    [1]  5  4 10  3  2  7  1  9  8

> Q. Can I generate more than ten random numbers from x=1:10?

We can set `replace` to `TRUE`

``` r
sample(1:10, size=12, replace = TRUE)
```

     [1]  3 10 10  9  1  5  7  1  7 10  1  3

> Q. Write code for the `sample()` function that will generate
> nucleotide sequences of 6 bp.

``` r
sequence.practice <- sample(c("A","G","C","T"), size = 6, replace = TRUE)
paste(sequence.practice, sep="")
```

    [1] "A" "T" "G" "C" "A" "G"

> Q. Now we have our snippet, write a function `generate_dna()` that
> returns a user specified length DNA sequence:

``` r
generate_dna <- function(b) {
  sample( c("A","G","C","T"), size = b, replace = TRUE)
}
generate_dna(12)
```

     [1] "C" "G" "A" "A" "T" "G" "C" "T" "C" "T" "A" "G"
