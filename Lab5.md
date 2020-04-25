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
