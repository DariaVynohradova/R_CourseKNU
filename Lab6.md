### Task 1
##### Create matrix of 5 columns and 10 rows using function rnorm(50)
```
> m <- matrix(rnorm(50), 10, 5)
```

### Task 2
##### Find max value of each column
```
> apply(m, 2, max)
[1] 1.306256 1.881243 1.289859 1.557702 2.439147
```

### Task 3
##### Find mean value of each column
```
> apply(m, 2, mean)
[1] 0.21411126 0.04322096 0.11872695 0.33961233 0.52974965
```

### Task 4
##### Find min value of each row
```
> apply(m, 1, min)
 [1] -1.2765101 -0.3513558 -0.7825641 -0.6451669 -1.9358077 -0.3304727 -0.7689795 -0.2974254 -1.4856839 -0.5284490
 ```

### Task 5
##### Apply sorting for each colunm
```
> apply(m, 2, sort)
             [,1]       [,2]       [,3]         [,4]       [,5]
 [1,] -1.93580768 -0.7825641 -0.6451669 -1.276510116 -1.4856839
 [2,] -0.61379398 -0.7689795 -0.5284490 -0.495552521 -0.2565513
 [3,] -0.14708588 -0.5515641 -0.4230686 -0.223358767  0.1098279
 [4,] -0.02191329 -0.3513558 -0.2974254 -0.001806807  0.1404303
 [5,]  0.26129388 -0.3304727  0.2577041  0.164457296  0.5915340
 [6,]  0.42453715  0.1022726  0.2754030  0.237071383  0.6728126
 [7,]  0.57459468  0.2050294  0.2947808  0.883881414  0.6986915
 [8,]  1.11611117  0.4303382  0.3654313  1.059291388  1.1816461
 [9,]  1.17692068  0.5982627  0.5982015  1.490947779  1.2056425
[10,]  1.30625591  1.8812429  1.2898587  1.557702205  2.4391467
```

### Task 6
##### Count values that are less than 0 for each column
```
> negative <- function(x){
+   sum(x<0)
+ }
```

```
> apply(m, 2, negative)
[1] 4 5 4 4 2
```

### Task 7
##### Output values TRUE, if there is value that is greater than 2 in the column, FALSE otherwise
```
> above_two <- function(x){
+   sum(x>2)>0
+ }
```

```
> apply(m, 2, above_two)
[1] FALSE FALSE FALSE FALSE  TRUE
```

### Task 8
#####  Create list1 <- list(observationA = c(1:5, 7:3), observationB = matrix(1:6, nrow=2))
```
> list1 <- list(observationA = c(1:5, 7:3), observationB = matrix(1:6, nrow=2))
> lapply(list1, sum)
$observationA
[1] 40

$observationB
[1] 21
```

### Task 9
#####  Find max and min values for each element of the list
###### LAPPLY
```
> lapply(list1, min)
$observationA
[1] 1

$observationB
[1] 1
>
> lapply(list1, max)
$observationA
[1] 7

$observationB
[1] 6
```
###### SAPPLY
```
> sapply(list1, min)
observationA observationB 
           1            1 
> 
> sapply(list1, max)
observationA observationB 
           7            6 
```
