### Part I
##### Dataframe preparation
```
> prepare_set <- function(file_name) { 
+   df <- read.csv(file_name, skip = 1, 
+                  header = TRUE, encoding='UTF-8', 
+                  stringsAsFactors = FALSE) 
+   names(df) <- 'Country'
+   t<- length(colnames(df[1]))
+   for (i in 1:t) {
+     colnames(df)=sub("X..", "", colnames(df), fixed=TRUE)
+     colnames(df)=sub("X01..", "Gold", colnames(df))
+     colnames(df)=sub("X02..", "Silver", colnames(df))
+     colnames(df)=sub("X03..", "Bronze", colnames(df))
+   }
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

### Part II
##### Read census.csv
```
> census <- read.csv("C:/mylib/census.csv", stringsAsFactors = FALSE)
> head(census, 5)
 SUMLEV REGION DIVISION STATE COUNTY  STNAME        CTYNAME CENSUS2010POP ESTIMATESBASE2010 POPESTIMATE2010
1     40      3        6     1      0 Alabama        Alabama       4779736           4780127         4785161
2     50      3        6     1      1 Alabama Autauga County         54571             54571           54660
3     50      3        6     1      3 Alabama Baldwin County        182265            182265          183193
4     50      3        6     1      5 Alabama Barbour County         27457             27457           27341
5     50      3        6     1      7 Alabama    Bibb County         22915             22919           22861
  POPESTIMATE2011 POPESTIMATE2012 POPESTIMATE2013 POPESTIMATE2014 POPESTIMATE2015 NPOPCHG_2010 NPOPCHG_2011
1         4801108         4816089         4830533         4846411         4858979         5034        15947
2           55253           55175           55038           55290           55347           89          593
3          186659          190396          195126          199713          203709          928         3466
4           27226           27159           26973           26815           26489         -116         -115
5           22733           22642           22512           22549           22583          -58         -128
  NPOPCHG_2012 NPOPCHG_2013 NPOPCHG_2014 NPOPCHG_2015 BIRTHS2010 BIRTHS2011 BIRTHS2012 BIRTHS2013 BIRTHS2014
1        14981        14444        15878        12568      14226      59689      59062      57938      58334
2          -78         -137          252           57        151        636        615        574        623
3         3737         4730         4587         3996        517       2187       2092       2160       2186
4          -67         -186         -158         -326         70        335        300        283        260
5          -91         -130           37           34         44        266        245        259        247
  BIRTHS2015 DEATHS2010 DEATHS2011 DEATHS2012 DEATHS2013 DEATHS2014 DEATHS2015 NATURALINC2010 NATURALINC2011
1      58305      11089      48811      48357      50843      50228      50330           3137          10878
2        600        152        507        558        583        504        467             -1            129
3       2240        532       1825       1879       1902       2044       1992            -15            362
4        269        128        319        291        294        310        309            -58             16
5        253         34        278        237        281        211        223             10            -12
  NATURALINC2012 NATURALINC2013 NATURALINC2014 NATURALINC2015 INTERNATIONALMIG2010 INTERNATIONALMIG2011
1          10705           7095           8106           7975                 1357                 4926
2             57             -9            119            133                   33                   20
3            213            258            142            248                   69                  187
4              9            -11            -50            -40                    2                   -4
5              8            -22             36             30                    2                   10
  INTERNATIONALMIG2012 INTERNATIONALMIG2013 INTERNATIONALMIG2014 INTERNATIONALMIG2015 DOMESTICMIG2010
1                 4904                 4834                 5529                 5726             537
2                   16                   16                   18                   19              49
3                  172                  170                  212                  221             856
4                   -7                   -3                   -2                    0             -62
5                   16                   18                   21                   21             -69
  DOMESTICMIG2011 DOMESTICMIG2012 DOMESTICMIG2013 DOMESTICMIG2014 DOMESTICMIG2015 NETMIG2010 NETMIG2011 NETMIG2012
1              11            -929            1838            2816           -2268       1894       4937       3975
2             398            -161            -166             125            -140         82        418       -145
3            2743            3327            4211            3799            3469        925       2930       3499
4            -129             -68            -191            -105            -281        -60       -133        -75
5            -126            -115            -140              -4               4        -67       -116        -99
  NETMIG2013 NETMIG2014 NETMIG2015 RESIDUAL2010 RESIDUAL2011 RESIDUAL2012 RESIDUAL2013 RESIDUAL2014 RESIDUAL2015
1       6672       8345       3458            3          132          301          677         -573         1135
2       -150        143       -121            8           46           10           22          -10           45
3       4381       4011       3690           18          174           25           91          434           58
4       -194       -107       -281            2            2           -1           19           -1           -5
5       -122         17         25           -1            0            0           14          -16          -21
  GQESTIMATESBASE2010 GQESTIMATES2010 GQESTIMATES2011 GQESTIMATES2012 GQESTIMATES2013 GQESTIMATES2014
1              116185          116212          115560          115666          116963          119088
2                 455             455             455             455             455             455
3                2307            2307            2307            2249            2304            2308
4                3193            3193            3382            3388            3389            3353
5                2224            2224            2224            2224            2224            2233
  GQESTIMATES2015 RBIRTH2011 RBIRTH2012 RBIRTH2013 RBIRTH2014 RBIRTH2015 RDEATH2011 RDEATH2012 RDEATH2013 RDEATH2014
1          119599   12.45302   12.28258   12.01208  12.056286   12.01497  10.183524  10.056360  10.541099  10.380963
2             455   11.57279   11.13848   10.41619  11.293597   10.84628   9.225478  10.106133  10.579514   9.136393
3            2309   11.82635   11.09652   11.20559  11.072868   11.10500   9.868812   9.966716   9.867141  10.353587
4            3352   12.27848   11.03245   10.45592   9.667584   10.09305  11.692048  10.701480  10.862337  11.526735
5            2236   11.66820   10.79890   11.47185  10.962917   11.21156  12.194587  10.446281  12.446295   9.365083
  RDEATH2015 RNATURALINC2011 RNATURALINC2012 RNATURALINC2013 RNATURALINC2014 RNATURALINC2015 RINTERNATIONALMIG2011
1  10.371556       2.2694961       2.2262204       1.4709812       1.6753223        1.643417             1.0277200
2   8.442022       2.3473111       1.0323469      -0.1633201       2.1572040        2.404259             0.3639242
3   9.875515       1.9575398       1.1298086       1.3384450       0.7192805        1.229482             1.0112153
4  11.593877       0.5864350       0.3309736      -0.4064140      -1.8591507       -1.500825            -0.1466088
5   9.882124      -0.5263851       0.3526171      -0.9744430       1.5978340        1.329434             0.4386542
  RINTERNATIONALMIG2012 RINTERNATIONALMIG2013 RINTERNATIONALMIG2014 RINTERNATIONALMIG2015 RDOMESTICMIG2011
1             1.0198398             1.0022161            1.14271613             1.1799629      0.002294949
2             0.2897816             0.2903469            0.32629976             0.3434656      7.242091472
3             0.9123337             0.8819211            1.07385542             1.0956269     14.832960211
4            -0.2574239            -0.1108402           -0.07436603             0.0000000     -4.728132388
5             0.7052342             0.7972716            0.93206986             0.9306036     -5.527043032
  RDOMESTICMIG2012 RDOMESTICMIG2013 RDOMESTICMIG2014 RDOMESTICMIG2015 RNETMIG2011 RNETMIG2012 RNETMIG2013
1       -0.1931956         0.381066        0.5820019       -0.4673692    1.030015   0.8266442    1.383282
2       -2.9159271        -3.012349        2.2659706       -2.5307989    7.606016  -2.6261455   -2.722002
3       17.6472928        21.845705       19.2432865       17.1978722   15.844176  18.5596266   22.727626
4       -2.5006895        -7.056824       -3.9042166      -10.5432988   -4.874741  -2.7581135   -7.167664
5       -5.0688705        -6.201001       -0.1775371        0.1772578   -5.088389  -4.3636364   -5.403729
  RNETMIG2014 RNETMIG2015
1   1.7247181   0.7125937
2   2.5922703  -2.1873334
3  20.3171419  18.2934991
4  -3.9785826 -10.5432988
5   0.7545327   1.1078614
```

##### Question 5
```
> quest5<-function() {
+   census_1<-split(census[ , "CTYNAME"], census[ , "STNAME"])
+   count<-sapply(census_1, length)
+   which.max(count)
+ }
> 
> quest5()
Texas
```

##### Question 6
```
> quest6<-function() {
+   census_2<-census[order(census$STNAME, -census$CENSUS2010POP), ]
+   df_split<-split(census_2, census_2$STNAME)
+   df_split<-lapply(df_split, function (x) sum (x[2:4, "CENSUS2010POP"]))
+   df_split<-df_split[order(unlist(df_split), decreasing = TRUE, na.last = TRUE)]
+   names(df_split) [1:3]
+ }
> quest6() 
[1] "California" "Texas" "Illinois"
```

##### Question 7
```
> quest7<-function() {
+   census_<-census[-which(census$COUNTY == 0), ]
+   population<-census_[, 10:15]
+   popul_max<-apply(population, 1, max)
+   popul_min<-apply(population, 1, min)
+   popul_chg<-(popul_max-popul_min)
+   population<-cbind(CTYNAME = census_$CTYNAME, popul_chg)
+   population[which.max(popul_chg)]
+ }
> quest7()
[1] "Harris County"
```

##### Question 8
```
> quest8 <- function() {
+   subset_1<-subset(census, (REGION==1 | REGION==2))
+   subset_2<-subset_1[grep("Washington", subset_1$CTYNAME),]
+   subset_3<-subset(subset_2, POPESTIMATE2015>POPESTIMATE2014)
+   subset_3[ , c("STNAME", "CTYNAME")]
+ }
> quest8() 
           STNAME           CTYNAME
897          Iowa Washington County
1420    Minnesota Washington County
2346 Pennsylvania Washington County
2356 Rhode Island Washington County
3164    Wisconsin Washington County
```

