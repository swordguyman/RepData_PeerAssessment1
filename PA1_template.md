# Reproducible Research: Peer Assessment 1

## Loading and preprocessing the data

```r
new <- read.csv('./activity.csv')
```

## What is mean total number of steps taken per day?
Create new data set by aggregating by day the number of steps.

```r
totalsteps <-aggregate(new[,1], by=list(new[,2]), FUN=sum, na.rm=TRUE)
```

Plotting total number of steps per day.

```r
plot(x=as.Date(totalsteps[,1]),y=totalsteps[,2],type='h',
main='Total Number of Steps per Day',ylab='Number of Steps',xlab='Date',lwd=6)
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

Data frame with mean number of steps per day.

```r
meanperday <- aggregate(new[,1], by=list(new[,2]), FUN=mean, na.rm=TRUE)
colnames(meanperday) <- c('Date','Mean')
meanperday
```

```
##          Date    Mean
## 1  2012-10-01     NaN
## 2  2012-10-02  0.4375
## 3  2012-10-03 39.4167
## 4  2012-10-04 42.0694
## 5  2012-10-05 46.1597
## 6  2012-10-06 53.5417
## 7  2012-10-07 38.2465
## 8  2012-10-08     NaN
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
## 32 2012-11-01     NaN
## 33 2012-11-02 36.8056
## 34 2012-11-03 36.7049
## 35 2012-11-04     NaN
## 36 2012-11-05 36.2465
## 37 2012-11-06 28.9375
## 38 2012-11-07 44.7326
## 39 2012-11-08 11.1771
## 40 2012-11-09     NaN
## 41 2012-11-10     NaN
## 42 2012-11-11 43.7778
## 43 2012-11-12 37.3785
## 44 2012-11-13 25.4722
## 45 2012-11-14     NaN
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
## 61 2012-11-30     NaN
```

Data frame with median number of steps per day.

```r
medianperday <- aggregate(new[,1], by=list(new[,2]), FUN=median, na.rm=TRUE)
colnames(medianperday) <- c('Date','Median')
medianperday
```

```
##          Date Median
## 1  2012-10-01     NA
## 2  2012-10-02      0
## 3  2012-10-03      0
## 4  2012-10-04      0
## 5  2012-10-05      0
## 6  2012-10-06      0
## 7  2012-10-07      0
## 8  2012-10-08     NA
## 9  2012-10-09      0
## 10 2012-10-10      0
## 11 2012-10-11      0
## 12 2012-10-12      0
## 13 2012-10-13      0
## 14 2012-10-14      0
## 15 2012-10-15      0
## 16 2012-10-16      0
## 17 2012-10-17      0
## 18 2012-10-18      0
## 19 2012-10-19      0
## 20 2012-10-20      0
## 21 2012-10-21      0
## 22 2012-10-22      0
## 23 2012-10-23      0
## 24 2012-10-24      0
## 25 2012-10-25      0
## 26 2012-10-26      0
## 27 2012-10-27      0
## 28 2012-10-28      0
## 29 2012-10-29      0
## 30 2012-10-30      0
## 31 2012-10-31      0
## 32 2012-11-01     NA
## 33 2012-11-02      0
## 34 2012-11-03      0
## 35 2012-11-04     NA
## 36 2012-11-05      0
## 37 2012-11-06      0
## 38 2012-11-07      0
## 39 2012-11-08      0
## 40 2012-11-09     NA
## 41 2012-11-10     NA
## 42 2012-11-11      0
## 43 2012-11-12      0
## 44 2012-11-13      0
## 45 2012-11-14     NA
## 46 2012-11-15      0
## 47 2012-11-16      0
## 48 2012-11-17      0
## 49 2012-11-18      0
## 50 2012-11-19      0
## 51 2012-11-20      0
## 52 2012-11-21      0
## 53 2012-11-22      0
## 54 2012-11-23      0
## 55 2012-11-24      0
## 56 2012-11-25      0
## 57 2012-11-26      0
## 58 2012-11-27      0
## 59 2012-11-28      0
## 60 2012-11-29      0
## 61 2012-11-30     NA
```

## What is the average daily activity pattern?
Constructing new data frame by aggregating by time interval the number of steps.

```r
avedailypattern <-aggregate(new[,1], by=list(new[,3]), FUN=mean, na.rm=TRUE)
```

Plotting time series.

```r
plot(x=avedailypattern[,1],y=avedailypattern[,2],type='l',
main='Average Number of Steps Across All Days per Interval',
ylab='Average Number of Steps',xlab='Daily Five Minute Interval',lwd=2)
```

![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7.png) 

5-minute interval with highest number of steps.

```r
avedailypattern[avedailypattern[,2]==max(avedailypattern[,2]),][1,1]
```

```
## [1] 835
```

## Imputing missing values
Total number of NA's.

```r
sum(is.na(new[,1]))
```

```
## [1] 2304
```

Reading in same file but with a different name. Now we modify the dataset by using a for loop to identify the NA's within the dataset and changing them to a new value. The method I used is to replace the NA with its corresponding mean number of steps by time interval, which was done in the previous question.

On a techinical note, the for loop for the i's refers to the number of days and the for loop for the j's refers to the 5-minute time intervals.

```r
newer <- read.csv('./activity.csv')
for(i in 1:nrow(totalsteps)){
  for(j in 1:nrow(avedailypattern)){
		if(is.na(newer[j+(i-1)*nrow(avedailypattern),1]) == TRUE){
			newer[j+(i-1)*nrow(avedailypattern),1] <- avedailypattern[j,2]
		}
	}
}
```

Exact repeat of the second question, except with NA's removed. Create new data set by aggregating by days the number of steps.

```r
totalsteps2 <-aggregate(newer[,1], by=list(newer[,2]), FUN=sum, na.rm=TRUE)
```

Plotting histogram of total number of steps per day.

```r
plot(x=as.Date(totalsteps2[,1]),y=totalsteps2[,2],type='h',
main='Total Number of Steps per Day',ylab='Number of Steps',xlab='Date',lwd=6)
```

![plot of chunk unnamed-chunk-12](figure/unnamed-chunk-12.png) 

Data frame with mean number of steps per day.

```r
meanperday2 <- aggregate(newer[,1], by=list(newer[,2]), FUN=mean, na.rm=TRUE)
colnames(meanperday) <- c('Date','Mean')
meanperday2
```

```
##       Group.1       x
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

Data frame with median number of steps per day.

```r
medianperday2 <- aggregate(newer[,1], by=list(newer[,2]), FUN=median, na.rm=TRUE)
colnames(medianperday) <- c('Date','Median')
medianperday2
```

```
##       Group.1     x
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

## Are there differences in activity patterns between weekdays and weekends?
Creating new data frame with a factor variable, which splits the data frame between weekdays and weekends. We first create an empty data frame for the for loop, and then look at our data frame's data column to identify and group them into their appropriate factor groups. Last, we combine via columns.

```r
Factor <- data.frame(rep(NA,length(new[,1])))
for(i in 1:length(new[,1])){
  if(weekdays(as.Date(new[i,2])) == c('Saturday') | weekdays(as.Date(new[i,2])) == c('Sunday')){
		Factor[i,1] <- (c('Weekend'))
	}
	else{
		Factor[i,1] <- (c('Weekday'))
	}
}
final <- cbind(new,Factor)
```

Create new data frame by aggregating by time interval AND the new factor variable the number of steps. Rename columns to be more readable. Construct more data frames according to their factor.

```r
avedailypattern2 <-aggregate(final[,1], by=list(final[,3],final[,4]), FUN=mean, na.rm=TRUE)
colnames(avedailypattern2) <- c('interval','factor','mean steps')
weekdays <- avedailypattern2[avedailypattern2$factor == 'Weekday',]
weekends <- avedailypattern2[avedailypattern2$factor == 'Weekend',]
```

Using the regular plotting system in R, we tell R we want two plots in one screen. Then we plot both time series, first the weekdays and then the weekends.

```r
par(mfrow=c(2,1))
plot(x=weekdays[,1],y=weekdays[,3],type='l',
main='Average Number of Steps Across Weekdays per Interval',
ylab='Average Number of Steps',xlab='Daily Five Minute Interval',lwd=2)
plot(x=weekends[,1],y=weekends[,3],type='l',
main='Average Number of Steps Across Weekends per Interval',
ylab='Average Number of Steps',xlab='Daily Five Minute Interval',lwd=2)
```

![plot of chunk unnamed-chunk-17](figure/unnamed-chunk-17.png) 
