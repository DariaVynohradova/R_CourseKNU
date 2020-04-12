### Task 1
##### Extract names of the colunms
```
 names(df)
[1] "Ozone"   "Solar.R" "Wind"    "Temp"    "Month"   "Day" 
```
### Task 2
##### Display first six rows of the data frame
```
> head(df, 6)
  Ozone Solar.R Wind Temp Month Day
1    41     190  7.4   67     5   1
2    36     118  8.0   72     5   2
3    12     149 12.6   74     5   3
4    18     313 11.5   62     5   4
5    NA      NA 14.3   56     5   5
6    28      NA 14.9   66     5   6
```
### Task 3
##### Display number of observations in the data frame
```
> nrow(df)
[1] 153
```
### Task 4
##### Display last 10 rows of the data frame
```
> tail(df, 10)
    Ozone Solar.R Wind Temp Month Day
144    13     238 12.6   64     9  21
145    23      14  9.2   71     9  22
146    36     139 10.3   81     9  23
147     7      49 10.3   69     9  24
148    14      20 16.6   63     9  25
149    30     193  6.9   70     9  26
150    NA     145 13.2   77     9  27
151    14     191 14.3   75     9  28
152    18     131  8.0   76     9  29
153    20     223 11.5   68     9  30
```
### Task 5
##### Count number of missing values in "Ozone" column
```
> sum(is.na(df$Ozone))
[1] 37
```
### Task 6
##### Calculate mean value of "Ozone" column
```
> mean(df$Ozone, na.rm=TRUE)
[1] 42.12931
```
### Task 7
##### Create a subset, where "Ozone">31 and "Temp">90
```
> subdf<- subset(df, Ozone > 31 & Temp >90)
> subdf
    Ozone Solar.R Wind Temp Month Day
69     97     267  6.3   92     7   8
70     97     272  5.7   92     7   9
120    76     203  9.7   97     8  28
121   118     225  2.3   94     8  29
122    84     237  6.3   96     8  30
123    85     188  6.3   94     8  31
124    96     167  6.9   91     9   1
125    78     197  5.1   92     9   2
126    73     183  2.8   93     9   3
127    91     189  4.6   93     9   4
```
##### Calculate mean value of "Solar.R" column
```
> mean(subdf$Solar.R)
[1] 212.8
```
### Task 8
##### Calculate mean value of "Temp" if "Month"==6
```
> mean(df[df$Month==6,"Temp"])
[1] 79.1
```
### Task 9
##### Calculate max value of "Ozone" if "Month"==5
```
> max(df[df$Month==5,"Ozone"], na.rm=TRUE)
[1] 115
```
