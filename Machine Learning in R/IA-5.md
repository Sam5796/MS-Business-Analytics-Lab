Individual Assignment 5
================
Samarth
2025-03-28

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax
for authoring HTML, PDF, and MS Word documents. For more details on
using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that
includes both content as well as the output of any embedded R code
chunks within the document. You can embed an R code chunk like this:

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

## Including Plots

You can also embed plots, for example:

![](IA-5_files/figure-gfm/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.

\##Item 1, Loading Packages

``` r
library(naivebayes)
```

    ## Warning: package 'naivebayes' was built under R version 4.4.3

    ## naivebayes 1.0.0 loaded

    ## For more information please visit:

    ## https://majkamichal.github.io/naivebayes/

``` r
library(caret)
```

    ## Warning: package 'caret' was built under R version 4.4.3

    ## Loading required package: ggplot2

    ## Warning: package 'ggplot2' was built under R version 4.4.3

    ## Loading required package: lattice

``` r
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 4.4.3

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(pROC)
```

    ## Warning: package 'pROC' was built under R version 4.4.3

    ## Type 'citation("pROC")' for a citation.

    ## 
    ## Attaching package: 'pROC'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     cov, smooth, var

\##Item 2, Importing Data

``` r
appdata_tv <- read.csv("C:/Users/Sam/Desktop/UMass Sem II/655 ML for A/Assignments/Individual Assignment 5/Running App Data, Training & Validation.csv") 
appdata_test <- read.csv("C:/Users/Sam/Desktop/UMass Sem II/655 ML for A/Assignments/Individual Assignment 5/Running App Data, Test.csv") 
```

``` r
head(appdata_tv) ##shows first few rows of dataframe
```

    ##   runner_id africa south_america asia likes_per_day is_male marathons
    ## 1     36848      0             1    0         2.664       1         1
    ## 2       436      1             0    0         2.664       1         1
    ## 3    109672      0             0    0         2.664       1         1
    ## 4     73262      0             0    1         5.328       0         1
    ## 5     73260      0             0    1         2.664       1         1
    ## 6       437      1             0    0         3.996       1         4
    ##   ultramarathoner age distance_per_day premium_member
    ## 1               0  42         0.000000              0
    ## 2               0  46         0.000000              0
    ## 3               0  49         3.437333              0
    ## 4               0  33         5.290900              0
    ## 5               0  51         0.000000              0
    ## 6               0  39        15.750334              0

``` r
nrow(appdata_tv) ##shows number of rows in dataframe
```

    ## [1] 115265

``` r
head(appdata_test) ##shows first few rows of dataframe
```

    ##   runner_id africa south_america asia likes_per_day is_male marathons
    ## 1     73264      0             0    1         7.992       1         1
    ## 2       443      1             0    0         0.000       1         1
    ## 3     73269      0             0    1         2.664       1         1
    ## 4     73273      0             0    1         7.992       0         1
    ## 5     36862      0             1    0         9.324       1         2
    ## 6    109688      0             0    0        11.988       1         1
    ##   ultramarathoner age distance_per_day premium_member
    ## 1               0  53       19.3166330              0
    ## 2               0  37        0.6753333              0
    ## 3               0  53        9.2146664              0
    ## 4               0  35       11.6293000              0
    ## 5               0  37       10.7716670              0
    ## 6               0  70       16.6216660              0

``` r
nrow(appdata_test) ##shows number of rows in dataframe
```

    ## [1] 12849

\##Item 3, Preparing Dataset for Classification

``` r
appdata_tv$premium_member <- factor(appdata_tv$premium_member) ##Sets outcome variable as categorical
```

``` r
appdata_test$premium_member <- factor(appdata_test$premium_member) ##Sets outcome variable as categorical
```

\##Item 4, Assessing Outcome Variable Balance in Training & Validation

``` r
table(appdata_tv$premium_member) ##Shows how many records are in each possible value of the outcome variable
```

    ## 
    ##      0      1 
    ## 113815   1450

``` r
table(appdata_test$premium_member) ##Shows how many records are in each possible value of the outcome variable
```

    ## 
    ##     0     1 
    ## 12686   163

## In training & validation data 1450 observations are for premium members and 113815 observations are for non-premium members. This is a imbalanced dataset with significantly fewer premium members compared to non-premium members.

\##Item 5, Setting Random Seed

``` r
set.seed(1234)
```

\##Item 6a, Oversampling the Training & Validation Data

``` r
appdata_tv_1 <- appdata_tv[which(appdata_tv$premium_member==1), ] ##Extracts all rows of the data frame where the outcome variable = the least common class

appdata_tv_0 <- appdata_tv[which(appdata_tv$premium_member==0), ] ##Extracts all rows of the data frame where the outcome variable = the most common class

sample <- sample.int(n = nrow(appdata_tv_0), size = 1450, replace = F) ##extracts random subsample of rows from most common class subset that is the same size as the entire subset of the least common class
appdata_tv_0_REDUCED <- appdata_tv_0[sample,] ##Extract subsample of NUM_ROWS size from most common class dataframe

appdata_tv_OVERSAMPLED <- rbind(appdata_tv_1, appdata_tv_0_REDUCED) ##Yields oversampled data
```

\##Item 6b, Oversampling Check

``` r
head(appdata_tv_OVERSAMPLED)
```

    ##     runner_id africa south_america asia likes_per_day is_male marathons
    ## 8       36849      0             1    0         3.996       1         4
    ## 9       73261      0             0    1         3.996       1         4
    ## 125       475      1             0    0         2.664       1         1
    ## 344     73366      0             0    1         1.332       0         3
    ## 345    109778      0             0    0         1.332       0         3
    ## 347     36956      0             1    0         3.996       1         1
    ##     ultramarathoner age distance_per_day premium_member
    ## 8                 0  50         55.02790              1
    ## 9                 0  42         48.76460              1
    ## 125               0  32         54.78867              1
    ## 344               0  60         37.79267              1
    ## 345               0  65         35.10726              1
    ## 347               1  53         49.03867              1

``` r
nrow(appdata_tv_OVERSAMPLED)
```

    ## [1] 2900

## As we can see above, 2900 rows are present in oversampled training & validation dataframe.

\##Item 7, Data Partitioning

``` r
set.seed(1234) ##Setting random seed
sample <- sample.int(n = nrow(appdata_tv_OVERSAMPLED), size = nrow(appdata_tv_OVERSAMPLED)*0.80, replace = F)
appdata_TRAINING_SET <- appdata_tv_OVERSAMPLED[sample, ] ##Yields training dataset
appdata_VALIDATION_SET <- appdata_tv_OVERSAMPLED[-sample, ] ##Yields validation portion
```

``` r
head(appdata_TRAINING_SET)
```

    ##       runner_id africa south_america asia likes_per_day is_male marathons
    ## 79515     61409      0             1    0         7.992       1         1
    ## 42966     50151      0             1    0         2.664       0         2
    ## 15889     78186      0             0    1         7.992       1         1
    ## 72366     22784      1             0    0         5.328       1         3
    ## 27358      8936      1             0    0        10.656       1         1
    ## 77854    133705      0             0    0        11.988       0         1
    ##       ultramarathoner age distance_per_day premium_member
    ## 79515               0  35         70.36097              1
    ## 42966               0  25         52.02827              1
    ## 15889               0  51          0.21600              0
    ## 72366               0  30         58.63850              1
    ## 27358               0  19         59.45687              1
    ## 77854               0  41         10.16333              0

\##Item 8, Training Naïve Bayes Model

``` r
naivebayes_model <- naive_bayes(premium_member ~ . -runner_id, data = appdata_TRAINING_SET)
```

\##Item 9, Producing Probability Predictions on Validation & Test Data

``` r
VALIDATION_PREDICTIONS <- predict(naivebayes_model, appdata_VALIDATION_SET, type="prob") ##Produce predictions
```

    ## Warning: predict.naive_bayes(): more features in the newdata are provided as
    ## there are probability tables in the object. Calculation is performed based on
    ## features to be found in the tables.

``` r
appdata_VALIDATION_SET <- (cbind(appdata_VALIDATION_SET, VALIDATION_PREDICTIONS)) ##Save validation predictions into dataframe
names(appdata_VALIDATION_SET)[names(appdata_VALIDATION_SET) == "1"] <- "prob_1" ##Rename column appropriately
names(appdata_VALIDATION_SET)[names(appdata_VALIDATION_SET) == "0"] <- "prob_0" ##Rename column appropriately
```

``` r
TEST_PREDICTIONS <- predict(naivebayes_model, appdata_test, type="prob") ##Produce predictions
```

    ## Warning: predict.naive_bayes(): more features in the newdata are provided as
    ## there are probability tables in the object. Calculation is performed based on
    ## features to be found in the tables.

``` r
appdata_test <- (cbind(appdata_test, TEST_PREDICTIONS)) ##Save test predictions into dataframe
names(appdata_test)[names(appdata_test) == "1"] <- "prob_1" ##Rename column appropriately
names(appdata_test)[names(appdata_test) == "0"] <- "prob_0" ##Rename column appropriately
```

\##Item 10, Obtaining Test Data AUC

``` r
myroc <- roc(appdata_test$premium_member, appdata_test$prob_1) ##ROC curve data
```

    ## Setting levels: control = 0, case = 1

    ## Setting direction: controls < cases

``` r
auc(myroc) ##Print out AUC
```

    ## Area under the curve: 0.9754

## Test AUC (Area Under Curve) for out test data is 0.9754 (Close to 1) and it is an excellent AUC value. The model has near perfect ability to distinguise between premium member(1) and not a premium member(0). Which suggest strong predictive power.

\##Item 11, Selecting Probability Threshold Using the Test ROC Curve

``` r
rocdata<-coords(myroc,ret=c("threshold", "sensitivity", "accuracy", "precision","fpr")) ##Displays the ROC curve data; sensitivity, precision, and accuracy displayed with each probability threshold
```

``` r
ideal_thresholds <- rocdata[which(rocdata$sensitivity>=0.80 & rocdata$precision>=0.23), ] ##Extracts the ROC curve data that meets the specified constraints
ideal_thresholds
```

    ##       threshold sensitivity  accuracy precision        fpr
    ## 12277 0.9514314    0.809816 0.9632656 0.2303665 0.03476273
    ## 12278 0.9516120    0.809816 0.9633435 0.2307692 0.03468390
    ## 12279 0.9516551    0.809816 0.9634213 0.2311734 0.03460508
    ## 12280 0.9520391    0.809816 0.9634991 0.2315789 0.03452625
    ## 12281 0.9526475    0.809816 0.9635769 0.2319859 0.03444742
    ## 12282 0.9530408    0.809816 0.9636548 0.2323944 0.03436860
    ## 12283 0.9532000    0.809816 0.9637326 0.2328042 0.03428977
    ## 12284 0.9533600    0.809816 0.9638104 0.2332155 0.03421094
    ## 12285 0.9538115    0.809816 0.9638882 0.2336283 0.03413211
    ## 12286 0.9541453    0.809816 0.9639661 0.2340426 0.03405329
    ## 12287 0.9542825    0.809816 0.9640439 0.2344583 0.03397446
    ## 12288 0.9544895    0.809816 0.9641217 0.2348754 0.03389563
    ## 12289 0.9547112    0.809816 0.9641995 0.2352941 0.03381681
    ## 12290 0.9552477    0.809816 0.9642774 0.2357143 0.03373798
    ## 12291 0.9557186    0.809816 0.9643552 0.2361360 0.03365915
    ## 12292 0.9559357    0.809816 0.9644330 0.2365591 0.03358032
    ## 12293 0.9561467    0.809816 0.9645109 0.2369838 0.03350150
    ## 12294 0.9562357    0.809816 0.9645887 0.2374101 0.03342267
    ## 12295 0.9563343    0.803681 0.9645109 0.2360360 0.03342267
    ## 12296 0.9564716    0.803681 0.9645887 0.2364621 0.03334384
    ## 12297 0.9566149    0.803681 0.9646665 0.2368897 0.03326502

## 0.9562357 is the value of probability threshold for which sensitivity is greater than or equal to 0.80 and precision is greater than or equal to 0.23 and precision is maximum.

\##OPTIONAL EXTRA CREDIT

\##Classifying validation & test records according to a chosen
probability threshold

``` r
appdata_VALIDATION_SET <- appdata_VALIDATION_SET  %>% mutate(CLASSIFICATION = 1*(prob_1 >= 0.9562357))

appdata_test <- appdata_test  %>% mutate(CLASSIFICATION = 1*(prob_1 >= 0.9562357))
```

\##Evaluating classification performance on validation & test using
confusion matrices

``` r
validation_performance <- confusionMatrix(data=as.factor(appdata_VALIDATION_SET$CLASSIFICATION), reference = as.factor(appdata_VALIDATION_SET$premium_member),positive="1") ##Generate confusion matrix (based on probability cutoff)
validation_performance
```

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction   0   1
    ##          0 290  72
    ##          1   9 209
    ##                                           
    ##                Accuracy : 0.8603          
    ##                  95% CI : (0.8294, 0.8875)
    ##     No Information Rate : 0.5155          
    ##     P-Value [Acc > NIR] : < 2.2e-16       
    ##                                           
    ##                   Kappa : 0.7185          
    ##                                           
    ##  Mcnemar's Test P-Value : 5.623e-12       
    ##                                           
    ##             Sensitivity : 0.7438          
    ##             Specificity : 0.9699          
    ##          Pos Pred Value : 0.9587          
    ##          Neg Pred Value : 0.8011          
    ##              Prevalence : 0.4845          
    ##          Detection Rate : 0.3603          
    ##    Detection Prevalence : 0.3759          
    ##       Balanced Accuracy : 0.8568          
    ##                                           
    ##        'Positive' Class : 1               
    ## 

``` r
test_performance <- confusionMatrix(data=as.factor(appdata_test$CLASSIFICATION), reference = as.factor(appdata_test$premium_member),positive="1") ##Generate confusion matrix (based on probability cutoff)
test_performance
```

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction     0     1
    ##          0 12262    31
    ##          1   424   132
    ##                                           
    ##                Accuracy : 0.9646          
    ##                  95% CI : (0.9612, 0.9677)
    ##     No Information Rate : 0.9873          
    ##     P-Value [Acc > NIR] : 1               
    ##                                           
    ##                   Kappa : 0.3545          
    ##                                           
    ##  Mcnemar's Test P-Value : <2e-16          
    ##                                           
    ##             Sensitivity : 0.80982         
    ##             Specificity : 0.96658         
    ##          Pos Pred Value : 0.23741         
    ##          Neg Pred Value : 0.99748         
    ##              Prevalence : 0.01269         
    ##          Detection Rate : 0.01027         
    ##    Detection Prevalence : 0.04327         
    ##       Balanced Accuracy : 0.88820         
    ##                                           
    ##        'Positive' Class : 1               
    ## 

## Accuracy on the test data is 96.46%. That means 96.46% of total predictions (both premium member 1 and 0) are correct. Precision on the test data is 23.74%. It implies that 23.74% of predicted premium members as 1 were actually 1. The model has high overall accuracy but low precision, meaning it often falsely predicts positive cases.
