---
title: "CodeBook"
author: "Theresa"
date: "3/30/2020"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## R Markdown

Download the dataset
Dataset downloaded and extracted under the folder called UCI HAR Dataset

Assign each data to variables
features <- features.txt

The features selected for this database come from the accelerometer and gyroscope tAcc-XYZ and tGyro-XYZ.

activities <- activity_labels.txt 

List of activities performed when the corresponding measurements were taken and its codes (labels)

subject_test <- test/subject_test.txt 

contains test data of volunteer test subjects being observed

x_test <- test/X_test.txt 

contains recorded features test data

y_test <- test/y_test.txt 

contains test data of activities’code labels

subject_train <- test/subject_train.txt 

contains train data of subjects being observed

x_train <- test/X_train.txt 

contains recorded features train data

y_train <- test/y_train.txt 

contains train data of activities’code labels

Merges the training and the test sets to create one data set
X  is created by merging x_train and x_test using rbind() function

Y is created by merging y_train and y_test using rbind() function

Subject is created by merging subject_train and subject_test using rbind() function

Merged_Data is created by merging Subject, Y and X using cbind() function

Extracts only the measurements on the mean and standard deviation for each measurement

TidyData is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation for each measurement

Uses descriptive activity names to rename the activities in the data set

Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

Labels the data set with descriptive variable names
code column in TidyData renamed into activities
All Acc in column’s name replaced by accelerometer
All Gyro in column’s name replaced by gyroscope
All BodyBody in column’s name replaced by body
All Mag in column’s name replaced by magnitude
All start with character f in column’s name replaced by frequency
All start with character t in column’s name replaced by time

From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
FinalData is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.

Export FinalData into FinalData.txt file.
