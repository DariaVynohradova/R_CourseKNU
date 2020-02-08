### Task 1. Basic classes of objects:
```
> char <- "Hello_World"
> class(char)
[1] "character"
> num <- 5.9482
> num
[1] 5.9482
> class(num)
[1] "numeric"
> int <- 5021L
> class(int)
[1] "integer"
> cmpl <- 3 + 7i
> class(cmpl)
[1] "complex"
> l <- TRUE
> class(l)
[1] "logical"
> l
[1] TRUE
```
### Task 2. Creating Vectors:
```
> v1 <- c(5:75)
> v1
 [1]  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
[21] 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44
[41] 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64
[61] 65 66 67 68 69 70 71 72 73 74 75
> v2 <- c(3.14, 2.71, 0, 13)
> v2
[1]  3.14  2.71  0.00 13.00
> v3 <- rep(TRUE, 100)
> v3
  [1] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [13] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [25] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [37] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [49] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [61] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [73] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [85] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [97] TRUE TRUE TRUE TRUE
> class(v3)
[1] "logical"
```
### Task 3. Creating Matrices
```

