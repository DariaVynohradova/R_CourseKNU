### Task 1. Subsetting a Vector
```
> v <- rnorm(100)
```
##### Return the 10th element
```
> v[10]
[1] 0.04047706
```
##### Extract elements with indices from 10 to 20
```
> v[10:20]
 [1]  0.04047706 -0.21711778  1.64866233  0.07364408
 [5] -0.04660122  0.10609970 -0.43609014  0.47404580
 [9]  0.58268160 -0.29188679 -1.08731779
 ```
 ##### Extract 10 elements from the 20th
 ```
 v[20:29]
 [1] -1.08731779  0.17128803  0.03504635  0.98457086
 [5]  0.63168595  0.47143301 -0.57885042 -1.19570055
 [9] -1.02147076 -0.42913579
 ```
 ##### Extract elements that are greater than 0
 ```
 > v[v>0]
 [1] 0.6970029206 1.0213955475 0.5552863439 0.6639715627
 [5] 1.4774828233 0.7442306752 0.0501248179 0.0404770648
 [9] 1.6486623283 0.0736440800 0.1060996956 0.4740457953
[13] 0.5826816014 0.1712880301 0.0350463523 0.9845708642
[17] 0.6316859456 0.4714330089 1.0598920475 0.4656282026
[21] 0.9914705712 1.4899002927 1.1193787329 0.3573764527
[25] 1.3654593703 0.4827360018 0.7573413147 1.8257708146
[29] 1.4942839800 1.0051396353 0.1771997095 0.0539860590
[33] 3.0895393383 2.6746125259 1.5420699621 0.0006179961
[37] 0.1345171027 0.3983523730 0.8064653960 0.7404890504
[41] 0.7977786962 0.2868531060 0.5043795440 1.7996113485
[45] 0.0467632594 1.0291019518 0.2740728832 1.3255432222
[49] 0.9469439512 0.3181237307 0.2516723428 1.4551278503
[53] 1.0716629465 1.6481299730 0.2266186635 0.8206350687
[57] 0.6960320105 0.4933451491
```
### Task 2. Subsetting a Data Frame
```
> df <- data.frame(a = rnorm(100), b = 1:100, cc = sample(letters, 100, replace = TRUE))
```
##### Get last 10 rows
```
> tail(df, 10)
              a   b cc
91   0.70195366  91  x
92  -1.24964527  92  a
93  -1.27069864  93  s
94  -1.08204034  94  f
95  -1.07970714  95  r
96   0.09002789  96  e
97   2.04852764  97  q
98   0.38771860  98  x
99   0.90172857  99  w
100 -0.83272500 100  o
```
##### Exrtract rows from 10 to 20
```
> df[10:20,]
            a  b cc
10 -0.6272781 10  i
11 -0.1710023 11  l
12  0.9445532 12  j
13  0.8029673 13  f
14  0.1446388 14  t
15  0.2448631 15  c
16  0.3377043 16  h
17  1.2569623 17  k
18 -0.2781572 18  q
19  0.9476848 19  w
20 -1.6493332 20  x
```
##### Return the 10th element of the column 'b'
```
> df[[10,2]]
[1] 10
```
##### Extract column 'cc' using column name
```
df$cc
  [1] b l u f s s v b d i l j f t c h k q w x z r a s o
 [26] h j n i a c f s g q p t f t b f n q i d e i m c e
 [51] x e f z d r y f j f h a o d p a k u p p l o p p x
 [76] u u h e k n s y x y w z h k z x a s f r e q x w o
26 Levels: a b c d e f g h i j k l m n o p q r s ... z
```

```
> data.frame(df$cc)
    df.cc
1       b
2       l
3       u
4       f
5       s
6       s
7       v
8       b
9       d
10      i
11      l
12      j
13      f
14      t
15      c
16      h
17      k
18      q
19      w
20      x
21      z
22      r
23      a
24      s
25      o
26      h
27      j
28      n
29      i
30      a
31      c
32      f
33      s
34      g
35      q
36      p
37      t
38      f
39      t
40      b
41      f
42      n
43      q
44      i
45      d
46      e
47      i
48      m
49      c
50      e
51      x
52      e
53      f
54      z
55      d
56      r
57      y
58      f
59      j
60      f
61      h
62      a
63      o
64      d
65      p
66      a
67      k
68      u
69      p
70      p
71      l
72      o
73      p
74      p
75      x
76      u
77      u
78      h
79      e
80      k
81      n
82      s
83      y
84      x
85      y
86      w
87      z
88      h
89      k
90      z
91      x
92      a
93      s
94      f
95      r
96      e
97      q
98      x
99      w
100     o
```
### Task 3. NA Values
```
> z<- c(1, 2, 3, NA, 4, NA, 5, NA)
> z
[1]  1  2  3 NA  4 NA  5 NA
```
##### Return all the elements that are not NA
```
> nas <- is.na(z)
> z[!nas]
[1] 1 2 3 4 5
```
##### Calculate mean of the elemetns without NAs
```
> mean(z, na.rm=TRUE)
[1] 3
```
##### Calculate mean of the elemetns with NAs
na.rm = FALSE does not remove NA values present in vector before calculation proceeds. If NA is present in the vector, mean would be NA irrespective of anything else
```
> mean(z, na.rm=FALSE)
[1] NA
```
