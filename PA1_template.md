# Reproducible Research: Peer Assessment 1
I did not have time to complete the assignment. I did what I could for the first few problems.

## Loading and preprocessing the data
Here I create a data set 'final' where there are only two variables: number of steps and date, where date is of class POSIXct, POSIXlt. I was not sure if I needed this or not, but seeing as how I did not complete the assignment, the world will never know.
```{r}
setwd('C:/Users/Roberto/Desktop/Data Science Coursera/Reproducible Research Course Project 1')
new <- read.csv('./activity.csv')
new[,2] <- as.character(new[,2])
newcol <- rep(NA,length(new[,3]))
for(i in 1:length(new[,3])){
  if(new[i,3] <= 9){
		newcol[i] <- paste('00:0',new[i,3],':00',sep='')
	}
	else if(new[i,3] >= 10 && new[i,3] <=99){
		newcol[i] <- paste('00:',new[i,3],':00',sep='')	
	} 	
	else if(new[i,3] >= 100 && new[i,3] <= 999){
		newcol[i] <- paste('0',substr(new[i,3],1,1),':',substr(new[i,3],2,3),':00',sep='')
	}
	else{
		newcol[i] <- paste(substr(new[i,3],1,2),':',substr(new[i,3],3,4),':00',sep='')
	}
}
newercol <- data.frame(rep(NA,length(new[,3])))
for(i in 1:length(new[,3])){
	newercol[i,1] <- paste(new[i,2],newcol[i])
}
Date <- strptime(newercol[,1],format='%Y-%m-%d %H:%M:%S')
dummy <- as.data.frame(new[,1])
final <- cbind(Date,dummy)
```


## What is mean total number of steps taken per day?
This was the closest histogram I could make without using the hist() function, which I did not know how to utilize to get the right plot.
```{r}
totalsteps <-aggregate(new[,1], by=list(new[,2]), FUN=sum, na.rm=TRUE)

plot(x=as.Date(totalsteps[,1]),y=totalsteps[,2],type='h',
main='Total Number of Steps per Day',ylab='Number of Steps',xlab='Date',lwd=6)
```

Here are the mean and median per day. Median seems to be screwed up and I have no idea why.
```{r}
meanperday <- aggregate(new[,1], by=list(new[,2]), FUN=mean, na.rm=TRUE)

medianperday <- aggregate(new[,1], by=list(new[,2]), FUN=median, na.rm=TRUE)
meanperday
medianperday
```
## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
