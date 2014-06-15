Assignment 1
========================================================

Loading and preprocessing data

Downloadig the data file and unzipping it to a "data" directory


```r
library(reshape2)
library(lattice)
if(!file.exists("./data")){dir.create("./data")}

activity <- read.csv("./data/activity.csv")
```


Processing and transforming the dataset by changing the date variable to type "date"

```r
activity$date=as.Date(activity$date)
```

What is mean total number of steps taken per day?

1. Calculating and reporting the total number of steps per day by using the melt and dcast functions

```r
activity_melt=melt(activity, id=c("date"), measure.vars=c("steps"))
activityMeltCastSum=dcast(activity_melt, date~variable, sum)
```

Histogram showing the number of distribution of the total number of steps per day

```r
hist(activityMeltCastSum[,2], breaks=50, xlab="Average number of steps per day", main="Distribution of average steps per day")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

2. Calculating the average number of steps per day by using the melt and dcast functions and reporting the average number of steps per day by using the summary functiion

```r
activityMeltCastMean=dcast(activity_melt, date~variable, mean)
summary(activityMeltCastMean)
```

```
##       date                steps      
##  Min.   :2012-10-01   Min.   : 0.14  
##  1st Qu.:2012-10-16   1st Qu.:30.70  
##  Median :2012-10-31   Median :37.38  
##  Mean   :2012-10-31   Mean   :37.38  
##  3rd Qu.:2012-11-15   3rd Qu.:46.16  
##  Max.   :2012-11-30   Max.   :73.59  
##                       NA's   :8
```

```r
activityMeltCastMean
```

```
##          date   steps
## 1  2012-10-01      NA
## 2  2012-10-02  0.4375
## 3  2012-10-03 39.4167
## 4  2012-10-04 42.0694
## 5  2012-10-05 46.1597
## 6  2012-10-06 53.5417
## 7  2012-10-07 38.2465
## 8  2012-10-08      NA
## 9  2012-10-09 44.4826
## 10 2012-10-10 34.3750
## 11 2012-10-11 35.7778
## 12 2012-10-12 60.3542
## 13 2012-10-13 43.1458
## 14 2012-10-14 52.4236
## 15 2012-10-15 35.2049
## 16 2012-10-16 52.3750
## 17 2012-10-17 46.7083
## 18 2012-10-18 34.9167
## 19 2012-10-19 41.0729
## 20 2012-10-20 36.0938
## 21 2012-10-21 30.6285
## 22 2012-10-22 46.7361
## 23 2012-10-23 30.9653
## 24 2012-10-24 29.0104
## 25 2012-10-25  8.6528
## 26 2012-10-26 23.5347
## 27 2012-10-27 35.1354
## 28 2012-10-28 39.7847
## 29 2012-10-29 17.4236
## 30 2012-10-30 34.0938
## 31 2012-10-31 53.5208
## 32 2012-11-01      NA
## 33 2012-11-02 36.8056
## 34 2012-11-03 36.7049
## 35 2012-11-04      NA
## 36 2012-11-05 36.2465
## 37 2012-11-06 28.9375
## 38 2012-11-07 44.7326
## 39 2012-11-08 11.1771
## 40 2012-11-09      NA
## 41 2012-11-10      NA
## 42 2012-11-11 43.7778
## 43 2012-11-12 37.3785
## 44 2012-11-13 25.4722
## 45 2012-11-14      NA
## 46 2012-11-15  0.1424
## 47 2012-11-16 18.8924
## 48 2012-11-17 49.7882
## 49 2012-11-18 52.4653
## 50 2012-11-19 30.6979
## 51 2012-11-20 15.5278
## 52 2012-11-21 44.3993
## 53 2012-11-22 70.9271
## 54 2012-11-23 73.5903
## 55 2012-11-24 50.2708
## 56 2012-11-25 41.0903
## 57 2012-11-26 38.7569
## 58 2012-11-27 47.3819
## 59 2012-11-28 35.3576
## 60 2012-11-29 24.4688
## 61 2012-11-30      NA
```

Calculating the average number of steps per day by using the melt and dcast functions and reporting the average number of steps per day by using the table and summary functiions

```r
activityMeltCastMedian=dcast(activity_melt, date~variable, median, fill=NaN)
activityMeltCastMedian
```

```
##          date steps
## 1  2012-10-01    NA
## 2  2012-10-02     0
## 3  2012-10-03     0
## 4  2012-10-04     0
## 5  2012-10-05     0
## 6  2012-10-06     0
## 7  2012-10-07     0
## 8  2012-10-08    NA
## 9  2012-10-09     0
## 10 2012-10-10     0
## 11 2012-10-11     0
## 12 2012-10-12     0
## 13 2012-10-13     0
## 14 2012-10-14     0
## 15 2012-10-15     0
## 16 2012-10-16     0
## 17 2012-10-17     0
## 18 2012-10-18     0
## 19 2012-10-19     0
## 20 2012-10-20     0
## 21 2012-10-21     0
## 22 2012-10-22     0
## 23 2012-10-23     0
## 24 2012-10-24     0
## 25 2012-10-25     0
## 26 2012-10-26     0
## 27 2012-10-27     0
## 28 2012-10-28     0
## 29 2012-10-29     0
## 30 2012-10-30     0
## 31 2012-10-31     0
## 32 2012-11-01    NA
## 33 2012-11-02     0
## 34 2012-11-03     0
## 35 2012-11-04    NA
## 36 2012-11-05     0
## 37 2012-11-06     0
## 38 2012-11-07     0
## 39 2012-11-08     0
## 40 2012-11-09    NA
## 41 2012-11-10    NA
## 42 2012-11-11     0
## 43 2012-11-12     0
## 44 2012-11-13     0
## 45 2012-11-14    NA
## 46 2012-11-15     0
## 47 2012-11-16     0
## 48 2012-11-17     0
## 49 2012-11-18     0
## 50 2012-11-19     0
## 51 2012-11-20     0
## 52 2012-11-21     0
## 53 2012-11-22     0
## 54 2012-11-23     0
## 55 2012-11-24     0
## 56 2012-11-25     0
## 57 2012-11-26     0
## 58 2012-11-27     0
## 59 2012-11-28     0
## 60 2012-11-29     0
## 61 2012-11-30    NA
```

What is the average daily activity pattern?

1. Calculating and reporting the mean number of steps per interval

```r
activityMeltInterval=melt(activity, id=c("interval"), measure.vars=c("steps"))
activityMeltCastIntervalMean=dcast(activityMeltInterval, interval~variable, mean, na.rm=TRUE)


plot(activityMeltCastIntervalMean$interval, activityMeltCastIntervalMean$steps,type="l", xlab="Time interval", ylab="Mean number of steps")
```

![plot of chunk unnamed-chunk-6](figure/unnamed-chunk-6.png) 

2. Finding the interval with the max value by using the which.max function. The intervak with the max value is:

```r
activityMeltCastIntervalMean[which.max(activityMeltCastIntervalMean $steps), 1]
```

```
## [1] 835
```

Imputing missing values

1. Finding the total number of missing values by reinterating through all the rows in the dataset and checking the missing values in all the three variables

```r
count=0
for (i in 1:nrow(activity)){
  if (is.na(activity[i,]$steps) | is.na(activity[i,]$date) | is.na(activity[i,]$interval)) {
		count=count+1
	}
}
sum(!complete.cases(activity))
```

```
## [1] 2304
```

2. Imputing the missing values in the dataset by using the mean values for each interval.

```r
activityImputed=activity
for (i in 1:nrow(activityImputed)){
	if (is.na(activityImputed[i,]$steps)) {
		rowNumb=which(activityMeltCastIntervalMean$interval==activity[i,]$interval)
		activityImputed[i,]$steps= activityMeltCastIntervalMean[rowNumb,]$steps
	}
}
```

3. activityImputed is the new dataset containing the imputed values

4. Calculating the mean and median per day for the Imputed values

```r
activityImputedMelt=melt(activityImputed, id=c("date"), measure.vars=c("steps"))
activityImputedMeltCastSum=dcast(activityImputedMelt, date~variable, sum)
```

Histogram showing the number of distribution of the total number of steps per day

```r
hist(activityImputedMeltCastSum[,2], breaks=50, xlab="Average number of steps per day", main="Distribution of average steps per day")
```

![plot of chunk unnamed-chunk-11](figure/unnamed-chunk-11.png) 

Table reporting the average number of steps per day for Activity datase with the Imputed values

```r
activityImputedMeltCastMean=dcast(activityImputedMelt, date~variable, mean)
activityImputedMeltCastMean
```

```
##          date   steps
## 1  2012-10-01 37.3826
## 2  2012-10-02  0.4375
## 3  2012-10-03 39.4167
## 4  2012-10-04 42.0694
## 5  2012-10-05 46.1597
## 6  2012-10-06 53.5417
## 7  2012-10-07 38.2465
## 8  2012-10-08 37.3826
## 9  2012-10-09 44.4826
## 10 2012-10-10 34.3750
## 11 2012-10-11 35.7778
## 12 2012-10-12 60.3542
## 13 2012-10-13 43.1458
## 14 2012-10-14 52.4236
## 15 2012-10-15 35.2049
## 16 2012-10-16 52.3750
## 17 2012-10-17 46.7083
## 18 2012-10-18 34.9167
## 19 2012-10-19 41.0729
## 20 2012-10-20 36.0938
## 21 2012-10-21 30.6285
## 22 2012-10-22 46.7361
## 23 2012-10-23 30.9653
## 24 2012-10-24 29.0104
## 25 2012-10-25  8.6528
## 26 2012-10-26 23.5347
## 27 2012-10-27 35.1354
## 28 2012-10-28 39.7847
## 29 2012-10-29 17.4236
## 30 2012-10-30 34.0938
## 31 2012-10-31 53.5208
## 32 2012-11-01 37.3826
## 33 2012-11-02 36.8056
## 34 2012-11-03 36.7049
## 35 2012-11-04 37.3826
## 36 2012-11-05 36.2465
## 37 2012-11-06 28.9375
## 38 2012-11-07 44.7326
## 39 2012-11-08 11.1771
## 40 2012-11-09 37.3826
## 41 2012-11-10 37.3826
## 42 2012-11-11 43.7778
## 43 2012-11-12 37.3785
## 44 2012-11-13 25.4722
## 45 2012-11-14 37.3826
## 46 2012-11-15  0.1424
## 47 2012-11-16 18.8924
## 48 2012-11-17 49.7882
## 49 2012-11-18 52.4653
## 50 2012-11-19 30.6979
## 51 2012-11-20 15.5278
## 52 2012-11-21 44.3993
## 53 2012-11-22 70.9271
## 54 2012-11-23 73.5903
## 55 2012-11-24 50.2708
## 56 2012-11-25 41.0903
## 57 2012-11-26 38.7569
## 58 2012-11-27 47.3819
## 59 2012-11-28 35.3576
## 60 2012-11-29 24.4688
## 61 2012-11-30 37.3826
```

Table reporting the median number of steps per day

```r
activityImputedMeltCastMedian=dcast(activityImputedMelt, date~variable, median, fill=NaN)
activityImputedMeltCastMedian
```

```
##          date steps
## 1  2012-10-01 34.11
## 2  2012-10-02  0.00
## 3  2012-10-03  0.00
## 4  2012-10-04  0.00
## 5  2012-10-05  0.00
## 6  2012-10-06  0.00
## 7  2012-10-07  0.00
## 8  2012-10-08 34.11
## 9  2012-10-09  0.00
## 10 2012-10-10  0.00
## 11 2012-10-11  0.00
## 12 2012-10-12  0.00
## 13 2012-10-13  0.00
## 14 2012-10-14  0.00
## 15 2012-10-15  0.00
## 16 2012-10-16  0.00
## 17 2012-10-17  0.00
## 18 2012-10-18  0.00
## 19 2012-10-19  0.00
## 20 2012-10-20  0.00
## 21 2012-10-21  0.00
## 22 2012-10-22  0.00
## 23 2012-10-23  0.00
## 24 2012-10-24  0.00
## 25 2012-10-25  0.00
## 26 2012-10-26  0.00
## 27 2012-10-27  0.00
## 28 2012-10-28  0.00
## 29 2012-10-29  0.00
## 30 2012-10-30  0.00
## 31 2012-10-31  0.00
## 32 2012-11-01 34.11
## 33 2012-11-02  0.00
## 34 2012-11-03  0.00
## 35 2012-11-04 34.11
## 36 2012-11-05  0.00
## 37 2012-11-06  0.00
## 38 2012-11-07  0.00
## 39 2012-11-08  0.00
## 40 2012-11-09 34.11
## 41 2012-11-10 34.11
## 42 2012-11-11  0.00
## 43 2012-11-12  0.00
## 44 2012-11-13  0.00
## 45 2012-11-14 34.11
## 46 2012-11-15  0.00
## 47 2012-11-16  0.00
## 48 2012-11-17  0.00
## 49 2012-11-18  0.00
## 50 2012-11-19  0.00
## 51 2012-11-20  0.00
## 52 2012-11-21  0.00
## 53 2012-11-22  0.00
## 54 2012-11-23  0.00
## 55 2012-11-24  0.00
## 56 2012-11-25  0.00
## 57 2012-11-26  0.00
## 58 2012-11-27  0.00
## 59 2012-11-28  0.00
## 60 2012-11-29  0.00
## 61 2012-11-30 34.11
```

Are there differences in activity patterns between weekdays and weekends?

1. Creating a new factor variable weekdays which holds vaules either "weekday" or "weekend"

```r
activityImputed$weekdays=weekdays(activityImputed$date)

weekdays=NULL
for (i in 1:nrow(activityImputed)){
	if ((activityImputed[i,]$weekdays=="Saturday") || (activityImputed[i,]$weekdays=="Sunday")) {
 		weekdays=c(weekdays,"weekend")
 	} else{
 		weekdays=c(weekdays,"weekday")
	}
}
activityImputed$weekdays=as.factor(weekdays)
```

2. Make a panel plot containing a time series plot (i.e. type = "l") of the 5-minute interval (x-axis)

```r
activityImputedMelt=melt(activityImputed, id=c("interval", "weekdays"), measure.vars=c("steps"))
activityImputedMeltCastMean=dcast(activityImputedMelt, interval+weekdays~variable, mean)

xyplot(steps~interval|weekdays, activityImputedMeltCastMean, xlab="Interval", ylab="Average number of steps", layout=c(1,3), type="l")
```

![plot of chunk unnamed-chunk-15](figure/unnamed-chunk-15.png) 

The plot shows that the average number of steps during the weekend is higher compared to the average number of steps during the weekday.





