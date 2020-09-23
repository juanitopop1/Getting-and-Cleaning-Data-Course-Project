---
title: "CodeBook"
output: html_notebook
This project run_analysis.R script demonstrate the 5 step required for collect, work with and clean an data set

  1.  Download the dataset:
  
        -Dataset downloaded and extracted under the folder called UCI HAR Dataset

  2.  Assign each data to variables:
  
        features <- features.txt : 561 obs, 2 variables.
        
        activities <- activity_labels.txt : 6 obs, 2 variables.
       
        subject_test <- test/subject_test.txt : 2947 obs, 1 variable
        
        x_test <- test/X_test.txt : 2947 obs, 561 variables
        
        y_test <- test/y_test.txt : 2947 obs, 1 variable
        
        subject_train <- test/subject_train.txt : 7352 obs, 1 variable
        
        x_train <- test/X_train.txt : 7352 obs, 561 variables
        
        y_train <- test/y_train.txt : 7352 obs, 1 variable
        

  3.  Merges the training and the test sets to create one data set:
  
        X (10299 obs, 561 variables) is created by merging x_train and x_test using rbind() function
        Y (10299 obs, 1 variable) is created by merging y_train and y_test using rbind() function
        Subject (10299 obs, 1 variable) is created by merging subject_train and subject_test using rbind() function
        Merged_Data (10299 obs, 563 variables) is created by merging Subject, Y and X using cbind()function

  4.  Extracts only the measurements on the mean and standard deviation for each measurement:
  
        TidyData (10299 obs, 88 variables) is created by subsetting Merged_Data, selecting only columns: subject, code 
		and the measurements on the mean and standard deviation (std) for each measurement

  5.  Uses descriptive activity names to name the activities in the data set:
  
        Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of 
		the activities variable

  6.  Appropriately labels the data set with descriptive variable names:
  
        code column in TidyData renamed into activities
        All Acc in column's name replaced by Accelerometer
        All Gyro in column's name replaced by Gyroscope
        All BodyBody in column's name replaced by Body
        All Mag in column's name replaced by Magnitude
        All start with character f in column's name replaced by Frequency
        All start with character t in column's name replaced by Time

  7.  From the data set in step 4, creates a second, independent tidy data set with the average of each variable
      for each activity and each subject:
		
        TextData (180 obs, 88 variables) is created by sumarizing TidyData taking the means of each variable for each 
		activity and each subject, after groupped by subject and activity.
        Export TextData into TextData.txt file.
---

This is an [R Markdown](http://rmarkdown.rstudio.com) Notebook. When you execute code within the notebook, the results appear beneath the code. 

Try executing this chunk by clicking the *Run* button within the chunk or by placing your cursor inside it and pressing *Ctrl+Shift+Enter*. 

Add a new chunk by clicking the *Insert Chunk* button on the toolbar or by pressing *Ctrl+Alt+I*.

When you save the notebook, an HTML file containing the code and output will be saved alongside it (click the *Preview* button or press *Ctrl+Shift+K* to preview the HTML file).

The preview shows you a rendered HTML copy of the contents of the editor. Consequently, unlike *Knit*, *Preview* does not run any R code chunks. Instead, the output of the chunk when it was last run in the editor is displayed.
