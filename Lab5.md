##### Set a new directory
```
> getwd()
[1] "C:/Users/HP/Documents"
> setwd("c:/specdata")
> getwd()
[1] "c:/specdata"
> file_list <- list.files()
> length(file_list)
[1] 332
```

### Task 1
##### Create function pmean() with three arguments
```
> pmean <- function(directory, pollutant, id=1:332){
+   file_list <- list.files()
+   values <- numeric()
+   for (i in id){
+     df <- read.csv(file_list[i])
+     values <- c(values, df[[pollutant]])
+   }
+   mean(values, na.rm=TRUE)
+ }
```
```
> pmean("specdata", "sulfate", 1:10)
[1] 4.064128
> pmean("specdata", "nitrate")
[1] 1.702932
> pmean("specdata", "sulfate", 55)
[1] 3.587319
```

### Task 2
##### Create function complete() that outputs the number of completely observed cases
```
> complete <- function(directory, id=1:332){
+   file_list <- list.files()
+   numobs <- numeric()
+   for (i in id){
+     df <- read.csv(file_list[i])
+     numobs <- c(numobs, sum(complete.cases(df)))
+   }
+   data.frame(id, numobs)
+ }
```
```
> complete("cpecdata", 1)
  id numobs
1  1    117
> complete("specdata", c(1, 4, 6, 34))
  id numobs
1  1    117
2  4    474
3  6    228
4 34    165
> complete("specdata", 35:45)
   id numobs
1  35    509
2  36    495
3  37    497
4  38    491
5  39    734
6  40     21
7  41    227
8  42     60
9  43     74
10 44    283
11 45    424
```

### Task 3
##### Create function corr() that returns the vector of correlation coefficients
```

