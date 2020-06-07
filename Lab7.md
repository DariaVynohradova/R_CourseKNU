### Part I
##### Dataframe preparation
```
> prepare_set <- function(file_name) { 
+   df <- read.csv(file_name, skip = 1, 
+                  header = TRUE, encoding='UTF-8', 
+                  stringsAsFactors = FALSE) 
+   names(df) <- c('Country', 'Summer', 'Gold', 'Silver', 'Bronze', 'Total', 'Winter', 
+                  'Gold.1', 'Silver.1', 'Bronze.1', 'Total.1', 
+                  'Games', 'Gold.2', 'Silver.2', 'Bronze.2', 'Combined.total') 
+   country_names <- strsplit(df$Country, "(", fixed = TRUE)
+   df$Country <- sapply(country_names, "[", 1)
+   df$ID <- substr(sapply(country_names, '[', 2), 1,3)
+   df <- df[-which(df$Country == 'Totals'), ]
+   df}
```
```
> olympics <- prepare_set("C:/mylib/olympics.csv")
> head(olympics, 5)
       Country Summer Gold Silver Bronze Total Winter Gold.1 Silver.1 Bronze.1 Total.1 Games Gold.2 Silver.2
1 Afghanistan      13    0      0      2     2      0      0        0        0       0    13      0        0
2     Algeria      12    5      2      8    15      3      0        0        0       0    15      5        2
3   Argentina      23   18     24     28    70     18      0        0        0       0    41     18       24
4     Armenia       5    1      2      9    12      6      0        0        0       0    11      1        2
5 Australasia       2    3      4      5    12      0      0        0        0       0     2      3        4
  Bronze.2 Combined.total  ID
1        2              2 AFG
2        8             15 ALG
3       28             70 ARG
4        9             12 ARM
5        5             12 ANZ
```

##### Question 1
```
> quest1<-function() {
+   olympics[which.max(olympics$Gold), "Country"]
+ }
> quest1()
[1] "United States"
```

##### Question 2
```
> quest2<-function() {
+   olympics[which.max(olympics$Total-olympics$Total.1), "Country"]
+ }
> quest2()
[1] "United States"
```

##### Question 3
```
> quest3<-function() {
+   my_subset<-subset(olympics, Gold>=1 & Gold.1>=1)
+   my_subset[which.max((my_subset$Gold-my_subset$Gold.1)/my_subset$Gold.2), "Country"]
+ }
> quest3()
[1] "Bulgaria"
```

##### Question 4
```
> quest4<-function() {
+   olympics$Points<-(olympics$Gold.2*3 + olympics$Silver.2*2 + olympics$Bronze.2*1)
+   olympics[, c("Country", "Points")]
+ }
> 
> head(quest4(), 5)
       Country Points
1 Afghanistan       2
2     Algeria      27
3   Argentina     130
4     Armenia      16
5 Australasia      22
```



