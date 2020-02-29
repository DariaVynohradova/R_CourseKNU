### Task 1
##### User defined function that returns the sum of two numbers
```
> a<--19
> b<-5

> add2<-function(x, y){mysum=x+y; mysum}
> add2(a, b)
[1] -14

> add2(34, 34.6)
[1] 68.6
```
### Task 2
##### User defined function that returns the vector of numbers that are greater default n=10
```
> v<-c(4, 5.6, -34, 15, 9.99, 12, 17.67)

> above<-function(v, n){nv<-v[v>n]; nv}
> above(v, 10)
[1] 15.00 12.00 17.67

> num<-3
> above(v, num)
[1]  4.00  5.60 15.00  9.99 12.00 17.67
```
### Task 3
##### User defined function with an expression
```
> my_ifelse <- function(x, exp, n){
+     if (exp == "<") {
+         x[x<n]
+     } else if(exp == "<="){
+         x[x<=n]
+     } else if (exp == ">"){
+         x[x>n]
+     } else if (exp == ">="){
+         x[x>=n]
+     } else if (exp == "=="){
+         x[x==n]
+     } else {
+         x} }

> v1<-c(7, 6.65, -5, 23, 0, 3.23, -0.45)

> my_ifelse(v1, '<', 4)
[1] -5.00  0.00  3.23 -0.45

> my_ifelse(v1, '==', 7)
[1] 7

> my_ifelse(v1, '<=', 2)
[1] -5.00  0.00 -0.45
```
### Task 4
##### User defined function that calculates mean value of the column
```
> c1<-c(3, NA, 8, 5, NA)
> c2<-1:5
> c3<-6:10
> c4<-11:15

> m<-rbind(c1, c2, c3, c4)
> m
   [,1] [,2] [,3] [,4] [,5]
c1    3   NA    8    5   NA
c2    1    2    3    4    5
c3    6    7    8    9   10
c4   11   12   13   14   15

+ colunmmean<-function(x, removeNA=TRUE){
+ colMeans(x, na.rm = removeNA)
+ }

> colunmmean(m)
[1]  5.25  7.00  8.00  8.00 10.00

> colunmmean(m, removeNA=FALSE)
[1] 5.25   NA 8.00 8.00   NA
```
