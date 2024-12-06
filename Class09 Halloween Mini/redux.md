# HAPPY HALLOWEEN Candy Miniproject from William Spookyface Bray


``` r
candy_file <- "candy-data.csv"
candy = read.csv(candy_file, row.names=1)
head(candy)
```

                 chocolate fruity caramel peanutyalmondy nougat crispedricewafer
    100 Grand            1      0       1              0      0                1
    3 Musketeers         1      0       0              0      1                0
    One dime             0      0       0              0      0                0
    One quarter          0      0       0              0      0                0
    Air Heads            0      1       0              0      0                0
    Almond Joy           1      0       0              1      0                0
                 hard bar pluribus sugarpercent pricepercent winpercent
    100 Grand       0   1        0        0.732        0.860   66.97173
    3 Musketeers    0   1        0        0.604        0.511   67.60294
    One dime        0   0        0        0.011        0.116   32.26109
    One quarter     0   0        0        0.011        0.511   46.11650
    Air Heads       0   0        0        0.906        0.511   52.34146
    Almond Joy      0   1        0        0.465        0.767   50.34755

``` r
nrow(candy)
```

    [1] 85

\#Question 1) There are 85 different kinds of candy!

``` r
table(candy$fruity)
```


     0  1 
    47 38 

# Question 2) There are 38 different kinds of fruity candy (in this case, the ‘1’ is tallying the presence of candy!

``` r
candy["Twix", ]$winpercent
```

    [1] 81.64291

\#cool example

``` r
candy["Charleston Chew", ]$winpercent
```

    [1] 38.97504

\#Question 3: I’m claiming/lying that Charleston Chew is my favorite
candy, even though it’s only really palatable when frozen. It has a win
percentage of 38.975

``` r
candy["Kit Kat", ]$winpercent
```

    [1] 76.7686

\#Question 4: 76.77% win or so..

``` r
candy["Tootsie Roll Snack Bars", ]$winpercent
```

    [1] 49.6535

\#Question 5: 49.635

``` r
library(dplyr)
```


    Attaching package: 'dplyr'

    The following objects are masked from 'package:stats':

        filter, lag

    The following objects are masked from 'package:base':

        intersect, setdiff, setequal, union

``` r
candy |> 
  filter(rownames(candy) %in% c("Dum Dums", "Twix")) |>
select(winpercent)
```

             winpercent
    Dum Dums   39.46056
    Twix       81.64291

``` r
library("skimr")
skim(candy)
```

|                                                  |       |
|:-------------------------------------------------|:------|
| Name                                             | candy |
| Number of rows                                   | 85    |
| Number of columns                                | 12    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |       |
| Column type frequency:                           |       |
| numeric                                          | 12    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |       |
| Group variables                                  | None  |

Data summary

**Variable type: numeric**

| skim_variable | n_missing | complete_rate | mean | sd | p0 | p25 | p50 | p75 | p100 | hist |
|:---|---:|---:|---:|---:|---:|---:|---:|---:|---:|:---|
| chocolate | 0 | 1 | 0.44 | 0.50 | 0.00 | 0.00 | 0.00 | 1.00 | 1.00 | ▇▁▁▁▆ |
| fruity | 0 | 1 | 0.45 | 0.50 | 0.00 | 0.00 | 0.00 | 1.00 | 1.00 | ▇▁▁▁▆ |
| caramel | 0 | 1 | 0.16 | 0.37 | 0.00 | 0.00 | 0.00 | 0.00 | 1.00 | ▇▁▁▁▂ |
| peanutyalmondy | 0 | 1 | 0.16 | 0.37 | 0.00 | 0.00 | 0.00 | 0.00 | 1.00 | ▇▁▁▁▂ |
| nougat | 0 | 1 | 0.08 | 0.28 | 0.00 | 0.00 | 0.00 | 0.00 | 1.00 | ▇▁▁▁▁ |
| crispedricewafer | 0 | 1 | 0.08 | 0.28 | 0.00 | 0.00 | 0.00 | 0.00 | 1.00 | ▇▁▁▁▁ |
| hard | 0 | 1 | 0.18 | 0.38 | 0.00 | 0.00 | 0.00 | 0.00 | 1.00 | ▇▁▁▁▂ |
| bar | 0 | 1 | 0.25 | 0.43 | 0.00 | 0.00 | 0.00 | 0.00 | 1.00 | ▇▁▁▁▂ |
| pluribus | 0 | 1 | 0.52 | 0.50 | 0.00 | 0.00 | 1.00 | 1.00 | 1.00 | ▇▁▁▁▇ |
| sugarpercent | 0 | 1 | 0.48 | 0.28 | 0.01 | 0.22 | 0.47 | 0.73 | 0.99 | ▇▇▇▇▆ |
| pricepercent | 0 | 1 | 0.47 | 0.29 | 0.01 | 0.26 | 0.47 | 0.65 | 0.98 | ▇▇▇▇▆ |
| winpercent | 0 | 1 | 50.32 | 14.71 | 22.45 | 39.14 | 47.83 | 59.86 | 84.18 | ▃▇▆▅▂ |

``` r
c("j", "K", "l") %in% c("x", "K", "d")
```

    [1] FALSE  TRUE FALSE

\#cool function bro!

``` r
candy |> 
  filter(winpercent > 75) |>
  filter(pricepercent < 0.5)
```

                       chocolate fruity caramel peanutyalmondy nougat
    Reese's Miniatures         1      0       0              1      0
                       crispedricewafer hard bar pluribus sugarpercent pricepercent
    Reese's Miniatures                0    0   0        0        0.034        0.279
                       winpercent
    Reese's Miniatures   81.86626

\#nice!

\#Question 6: The win percentage is quite large relative to the other
columns

\#Question 7: The ‘0’ and ‘1’ are the absence or presence of chocolate,
respectively!

``` r
hist(candy$winpercent)
```

![](redux_files/figure-commonmark/unnamed-chunk-12-1.png)

\#Question 8: two different ways; ggplot is the best

``` r
library(ggplot2)
```

    Warning: package 'ggplot2' was built under R version 4.4.2

``` r
ggplot(candy, aes(winpercent)) + geom_histogram(bins = 10) + theme_dark()
```

![](redux_files/figure-commonmark/unnamed-chunk-13-1.png)

\#Question 9: the distribution doesn’t appear to be symmetrical

``` r
summary(candy$winpercent)
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
      22.45   39.14   47.83   50.32   59.86   84.18 

\#Question 10 The center of the distribution is in fact below 50

``` r
candy$winpercent[as.logical(candy$chocolate)]
```

     [1] 66.97173 67.60294 50.34755 56.91455 38.97504 55.37545 62.28448 56.49050
     [9] 59.23612 57.21925 76.76860 71.46505 66.57458 55.06407 73.09956 60.80070
    [17] 64.35334 47.82975 54.52645 70.73564 66.47068 69.48379 81.86626 84.18029
    [25] 73.43499 72.88790 65.71629 34.72200 37.88719 76.67378 59.52925 48.98265
    [33] 43.06890 45.73675 49.65350 81.64291 49.52411

``` r
candy$winpercent[as.logical(candy$fruity)]
```

     [1] 52.34146 34.51768 36.01763 24.52499 42.27208 39.46056 43.08892 39.18550
     [9] 46.78335 57.11974 51.41243 42.17877 28.12744 41.38956 39.14106 52.91139
    [17] 46.41172 55.35405 22.44534 39.44680 41.26551 37.34852 35.29076 42.84914
    [25] 63.08514 55.10370 45.99583 59.86400 52.82595 67.03763 34.57899 27.30386
    [33] 54.86111 48.98265 47.17323 45.46628 39.01190 44.37552

``` r
inds <- as.logical(candy$chocolate)
candy[inds,]$winpecent
```

    NULL

\#huh

``` r
summary(candy$winpercent[as.logical(candy$chocolate)])
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
      34.72   50.35   60.80   60.92   70.74   84.18 

``` r
summary(candy$winpercent[as.logical(candy$fruity)])
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
      22.45   39.04   42.97   44.12   52.11   67.04 

\#Question 11: chocolate is definitely preferred!

``` r
t.test(summary(candy$winpercent[as.logical(candy$fruity)]), summary(candy$winpercent[as.logical(candy$chocolate)]))
```


        Welch Two Sample t-test

    data:  summary(candy$winpercent[as.logical(candy$fruity)]) and summary(candy$winpercent[as.logical(candy$chocolate)])
    t = -1.7099, df = 9.8118, p-value = 0.1187
    alternative hypothesis: true difference in means is not equal to 0
    95 percent confidence interval:
     -36.128100   4.800577
    sample estimates:
    mean of x mean of y 
     44.62086  60.28462 

\#hmmm, wrong

``` r
inds <- candy$chocolate ==1
choc.win <- candy[inds,]$winpercent

inds <- candy$fruity ==1
fruit.win <- candy[inds,]$winpercent
```

``` r
summary(fruit.win)
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
      22.45   39.04   42.97   44.12   52.11   67.04 

``` r
summary(choc.win)
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
      34.72   50.35   60.80   60.92   70.74   84.18 

``` r
t.test(fruit.win, choc.win)
```


        Welch Two Sample t-test

    data:  fruit.win and choc.win
    t = -6.2582, df = 68.882, p-value = 2.871e-08
    alternative hypothesis: true difference in means is not equal to 0
    95 percent confidence interval:
     -22.15795 -11.44563
    sample estimates:
    mean of x mean of y 
     44.11974  60.92153 

\#There we go! \#Question12: yes indeed it is significant

``` r
play <- c(2,1,5,3)
sort(play)
```

    [1] 1 2 3 5

``` r
play[order(play)]
```

    [1] 1 2 3 5

``` r
n <- c("d", "a")
n [order(n)]
```

    [1] "a" "d"

\#Cool function to remember!

``` r
sort(candy$winpercent)
```

     [1] 22.44534 23.41782 24.52499 27.30386 28.12744 29.70369 32.23100 32.26109
     [9] 33.43755 34.15896 34.51768 34.57899 34.72200 35.29076 36.01763 37.34852
    [17] 37.72234 37.88719 38.01096 38.97504 39.01190 39.14106 39.18550 39.44680
    [25] 39.46056 41.26551 41.38956 41.90431 42.17877 42.27208 42.84914 43.06890
    [33] 43.08892 44.37552 45.46628 45.73675 45.99583 46.11650 46.29660 46.41172
    [41] 46.78335 47.17323 47.82975 48.98265 49.52411 49.65350 50.34755 51.41243
    [49] 52.34146 52.82595 52.91139 54.52645 54.86111 55.06407 55.10370 55.35405
    [57] 55.37545 56.49050 56.91455 57.11974 57.21925 59.23612 59.52925 59.86400
    [65] 60.80070 62.28448 63.08514 64.35334 65.71629 66.47068 66.57458 66.97173
    [73] 67.03763 67.60294 69.48379 70.73564 71.46505 72.88790 73.09956 73.43499
    [81] 76.67378 76.76860 81.64291 81.86626 84.18029

\#I see, just giving me the win percent!

``` r
inds <- order(candy$winpercent)
head(candy[inds,])
```

                       chocolate fruity caramel peanutyalmondy nougat
    Nik L Nip                  0      1       0              0      0
    Boston Baked Beans         0      0       0              1      0
    Chiclets                   0      1       0              0      0
    Super Bubble               0      1       0              0      0
    Jawbusters                 0      1       0              0      0
    Root Beer Barrels          0      0       0              0      0
                       crispedricewafer hard bar pluribus sugarpercent pricepercent
    Nik L Nip                         0    0   0        1        0.197        0.976
    Boston Baked Beans                0    0   0        1        0.313        0.511
    Chiclets                          0    0   0        1        0.046        0.325
    Super Bubble                      0    0   0        0        0.162        0.116
    Jawbusters                        0    1   0        1        0.093        0.511
    Root Beer Barrels                 0    1   0        1        0.732        0.069
                       winpercent
    Nik L Nip            22.44534
    Boston Baked Beans   23.41782
    Chiclets             24.52499
    Super Bubble         27.30386
    Jawbusters           28.12744
    Root Beer Barrels    29.70369

\#Okay so that’s working fine… \#Question 13: The five least liked
candies are Nik L Nip, Boston Baked Beans, Chiclet, Super Bubble,
Jawbusters, Root Beer Barrels

``` r
inds <- order(candy$winpercent)
head(candy[rev(inds),])
```

                              chocolate fruity caramel peanutyalmondy nougat
    Reese's Peanut Butter cup         1      0       0              1      0
    Reese's Miniatures                1      0       0              1      0
    Twix                              1      0       1              0      0
    Kit Kat                           1      0       0              0      0
    Snickers                          1      0       1              1      1
    Reese's pieces                    1      0       0              1      0
                              crispedricewafer hard bar pluribus sugarpercent
    Reese's Peanut Butter cup                0    0   0        0        0.720
    Reese's Miniatures                       0    0   0        0        0.034
    Twix                                     1    0   1        0        0.546
    Kit Kat                                  1    0   1        0        0.313
    Snickers                                 0    0   1        0        0.546
    Reese's pieces                           0    0   0        1        0.406
                              pricepercent winpercent
    Reese's Peanut Butter cup        0.651   84.18029
    Reese's Miniatures               0.279   81.86626
    Twix                             0.906   81.64291
    Kit Kat                          0.511   76.76860
    Snickers                         0.651   76.67378
    Reese's pieces                   0.651   73.43499

# Question 14 Reese’s peanut butter and miniatures take the top two, followed by Twix, Kit Kat, Snickers and Reese’s Pieces

\#question 15:

``` r
library(ggplot2)

ggplot(candy) + 
  aes(winpercent, rownames(candy)) +
  geom_col()
```

![](redux_files/figure-commonmark/unnamed-chunk-30-1.png)

\#Doesn’t look too great \#Question 16:

``` r
ggplot(candy) + aes(x=winpercent, y=reorder(rownames(candy), winpercent)) + geom_col()
```

![](redux_files/figure-commonmark/unnamed-chunk-31-1.png)

\#Hey that’s in order now \# color your favorite candy!

``` r
my_cols=rep("black", nrow(candy))
my_cols[as.logical(candy$chocolate)] = "brown"
my_cols[as.logical(candy$bar)] = "purple"
my_cols[as.logical(candy$fruity)] = "pink"
my_cols[rownames(candy)=="Charleston Chew"] = "orange"

ggplot(candy) + 
  aes(winpercent, reorder(rownames(candy),winpercent)) +
  geom_col(fill=my_cols) 
```

![](redux_files/figure-commonmark/unnamed-chunk-32-1.png)

# If an individual (Charleston Chew) assignment came first it woud be overwritten, so the final bit should be last!

\#Question 17: Sixlets are the least popular form of chocolate, which is
not unfair \#Question 18: Starburst are justifiably beloved as the most
popular of otherwise pretty lousy fruity candies

\#Geom_text_repel is super useful below to separate

``` r
library(ggrepel)
ggplot(candy) +
  aes(winpercent, pricepercent, label=rownames(candy)) +
  geom_point(col=my_cols) + 
  geom_text_repel(col=my_cols, size=3.3, max.overlaps = 12)
```

    Warning: ggrepel: 12 unlabeled data points (too many overlaps). Consider
    increasing max.overlaps

![](redux_files/figure-commonmark/unnamed-chunk-33-1.png)

\#still a bit overplotted, but improved!

\#Question 19: Reese’s miniatures are a solid bet here

\#Question 20: Nik L Nip remains the least popula,yet most expensive

\#ooh a unique sorting situation here…

``` r
ord <- order(candy$pricepercent, decreasing = TRUE)
head( candy[ord,c(11,12)], n=5 )
```

                             pricepercent winpercent
    Nik L Nip                       0.976   22.44534
    Nestle Smarties                 0.976   37.88719
    Ring pop                        0.965   35.29076
    Hershey's Krackel               0.918   62.28448
    Hershey's Milk Chocolate        0.918   56.49050

# try corrplot to examine correlation structure

# 

``` r
ggplot(candy) +
  aes(pricepercent, reorder(rownames(candy), pricepercent)) +
  geom_segment(aes(yend = reorder(rownames(candy), pricepercent), 
                   xend = 0), col="blue") +
    geom_point()
```

![](redux_files/figure-commonmark/unnamed-chunk-35-1.png)

``` r
library(corrplot)
```

    corrplot 0.95 loaded

``` r
cij <- cor(candy)

corrplot(cij)
```

![](redux_files/figure-commonmark/unnamed-chunk-36-1.png)

\#how do we read this? -1 anticorrelated, +1 is positive correlation; so
fruity is anticorrelated with chocolate \#make a pca plot of the
situation

\#Question 22: Fruity and chocolate are quiet thoroughly anticorrelated
\#Question 23: Chocolate and win percentage are quite highly positively
correlated; per the hint chocolate fruity candies are fairly rare, and
so not popular

``` r
pca <- prcomp(candy, scale = TRUE)
summary(pca)
```

    Importance of components:
                              PC1    PC2    PC3     PC4    PC5     PC6     PC7
    Standard deviation     2.0788 1.1378 1.1092 1.07533 0.9518 0.81923 0.81530
    Proportion of Variance 0.3601 0.1079 0.1025 0.09636 0.0755 0.05593 0.05539
    Cumulative Proportion  0.3601 0.4680 0.5705 0.66688 0.7424 0.79830 0.85369
                               PC8     PC9    PC10    PC11    PC12
    Standard deviation     0.74530 0.67824 0.62349 0.43974 0.39760
    Proportion of Variance 0.04629 0.03833 0.03239 0.01611 0.01317
    Cumulative Proportion  0.89998 0.93832 0.97071 0.98683 1.00000

``` r
plot(pca$x[,1], pca$x[,2], col=my_cols)
```

![](redux_files/figure-commonmark/unnamed-chunk-38-1.png)

``` r
pca$rotation[,1]
```

           chocolate           fruity          caramel   peanutyalmondy 
          -0.4019466        0.3683883       -0.2299709       -0.2407155 
              nougat crispedricewafer             hard              bar 
          -0.2268102       -0.2215182        0.2111587       -0.3947433 
            pluribus     sugarpercent     pricepercent       winpercent 
           0.2600041       -0.1083088       -0.3207361       -0.3298035 

``` r
my_data <- cbind(candy, pca$x[,1:3])
```

``` r
w <- ggplot(my_data) + 
        aes(x=PC1, y=PC2, 
            size=winpercent/100,  
            text=rownames(my_data),
            label=rownames(my_data)) +
        geom_point(col=my_cols)

w
```

![](redux_files/figure-commonmark/unnamed-chunk-41-1.png)

``` r
library(ggrepel)

w + geom_text_repel(size=3.3, col=my_cols, max.overlaps = 7)  + 
  theme(legend.position = "none") +
  labs(title="Halloween Candy PCA",
       subtitle="Colored by type: chocolate bar (dark brown), chocolate other (light brown), fruity (red), other (black)",
       caption="Data from 538")
```

    Warning: ggrepel: 43 unlabeled data points (too many overlaps). Consider
    increasing max.overlaps

![](redux_files/figure-commonmark/unnamed-chunk-42-1.png)

``` r
par(mar=c(8,4,2,2))
barplot(pca$rotation[,1], las=2, ylab="PC1 Contribution")
```

![](redux_files/figure-commonmark/unnamed-chunk-43-1.png)

\#Question 24: Fruity, hard, and pluribus; this makes perfect sense,
given chocolate goes precisely the opposite direction of fruity, and
fruity candies are often sold in bag form… \#Plotly is pretty cool, but
alas, have to comment out

\#`{r} #library(plotly) #ggplotly(w)`
