### Task 1. Basic classes of objects
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
### Task 2. Creating Vectors
```
> v1 <- 5:75
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
##### Creating matrix from vector by adding a dimension attribute
```
> m1 <- c(0.5, 3.9, 0, 2, 1.3, 131, 2.2, 7, 3.5, 2.8, 4.6, 5.1)
> dim(m1) <- c(4, 3)
> m1
     [,1]  [,2] [,3]
[1,]  0.5   1.3  3.5
[2,]  3.9 131.0  2.8
[3,]  0.0   2.2  4.6
[4,]  2.0   7.0  5.1
```
##### Creating matrix using **matrix** function
```
> m2 <- matrix(c(0.5, 3.9, 0, 2, 1.3, 131, 2.2, 7, 3.5, 2.8, 4.6, 5.1), nrow = 4, ncol = 3)
> m2
     [,1]  [,2] [,3]
[1,]  0.5   1.3  3.5
[2,]  3.9 131.0  2.8
[3,]  0.0   2.2  4.6
[4,]  2.0   7.0  5.1
```
##### Creating matrix with rbind-ing
```
> x <- c(0.5, 1.3, 3.5)
> y <- c(3.9, 131, 2.8)
> z <- c(2, 7, 5.1)
> m2 <- rbind(x, y, z)
> m2
  [,1]  [,2] [,3]
x  0.5   1.3  3.5
y  3.9 131.0  2.8
z  2.0   7.0  5.1
```
### Task 4. Creating a list
```
> l_all_classes <- list(1L, "b", 365, FALSE, 3 + 6i)
> l_all_classes
[[1]]
[1] 1

[[2]]
[1] "b"

[[3]]
[1] 365

[[4]]
[1] FALSE

[[5]]
[1] 3+6i
```
### Task 5. Creating a factor with three levels
```
> f <- factor(c("baby", "child", "child", "baby", "adult", "adult", "child"), levels = c ("baby", "child", "adult"))
> f
[1] baby  child child baby  adult adult child
Levels: baby child adult
```
### Task 6. Identifying NAs
##### Defining an index of the first "NA"
```
> v_sub <- c(1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11)
> v_sub
 [1]  1  2  3  4 NA  6  7 NA  9 NA 11
> min(which(is.na(v_sub)))
[1] 5
```
##### Number of NAs 
```
> length(which(is.na(v_sub)))
[1] 3
```
### Task 7. Creating a data frame
```
> df <- data.frame(x = 35:40, y = c("M", "M", "F", "F", "F", "M"))
> df
   x y
1 35 M
2 36 M
3 37 F
4 38 F
5 39 F
6 40 M
```
### Task 8. Rename columns
```
> names(df) <- c("age", "gender")
> df
  age gender
1  35      M
2  36      M
3  37      F
4  38      F
5  39      F
6  40      M
```


