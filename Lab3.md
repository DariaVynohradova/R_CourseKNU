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
