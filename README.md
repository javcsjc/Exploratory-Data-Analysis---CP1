# Exploratory Data Analysis - Course Project#1
Data Science Specialization - Coursera

Original Dataset: https://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip

Project Objectives:

For each plot you should
* Construct the plot and save it to a PNG file with a width of 480 pixels and a height of 480 pixels.
* Name each of the plot files as plot1.png, plot2.png, etc.
* Create a separate R code file (plot1.R, plot2.R, etc.) that constructs the corresponding plot, i.e. code in plot1.R constructs the plot1.png plot. 
* Your code file should include code for reading the data so that the plot can be fully reproduced.
* You must also include the code that creates the PNG file.
* Add the PNG file and R code file to the top-level folder of your git repository (no need for separate sub-folders)

Assumptions:

* User has downloaded the "exdata data household_power_consumption.zip" file to local machine and has unzipped the file.
* Unzipped file name "household_power_consumption.txt" should reside on working directory.


## Start with a clean workspace
rm(list=ls()))

## Set working directory
setwd("/Users/AValdez/Desktop/Data Science Specialization - Coursera/datasciencecoursera/ExData_CP1")

## Load necessary libraries
library(plyr);
library(dplyr);
library(lubridate);

## Step #1 - Read data from household_power_consumption.txt file
## We get a data frame with dimensions of: 2075259 observations of 9 variables.
hpc <- read.csv("household_power_consumption.txt", sep=";", na.strings="?", stringsAsFactors=FALSE)

## Step #2 - We select the subsets that match the dates "1/2/2007" and "2/2/2007"
subset1 <- subset(hpc, hpc$Date == "1/2/2007"); ## Select dates that match "1/2/2007".
subset2 <- subset(hpc, hpc$Date == "2/2/2007"); ## Select dates that match "2/2/2007". 
## This newdataset has 2880 observations of 10 variables.
newdataset <- rbind(subset1, subset2); ## This new data set contains only data related to Feb. 1 and 2, 2007.

## Step #3 - Create a new variable "fulldatetime" that combines Date and Time
newdataset$fulldatetime <- paste(newdataset$Date, newdataset$Time, sep = " ");

## Step #4 - When combined Date and Time the resulting variable was still (chr). 
## We need to change to "POSIXlt"
newdataset$fulldatetime <- strptime(newdataset$fulldatetime, "%d/%m/%Y %H:%M:%S")

## Step #5 - I would like to rename the columns of the dataset and change their order
newdataset <- select(newdataset, date = Date, time = Time, fulldatetime, activepwr = Global_active_power, reactivepwr = Global_reactive_power, voltage = Voltage, intensity = Global_intensity, sub1 = Sub_metering_1, sub2 = Sub_metering_2, sub3 = Sub_metering_3)

## New Order is:
## date: (chr) Date in format dd/mm/yyyy
## time: (chr) Time in format hh:mm:ss
## fulldatetime: (POSIXlt) Date and time in the format yyyy-mm-dd hh:mm:ss
## activepwr: (num) household global minute-averaged active power (in kilowatt)
## reactivepwr: (num) household global minute-averaged reactive power (in kilowatt)
## voltage: (num) minute-averaged voltage (in volt)
## intensity: (num) household global minute-averaged current intensity (in ampere)
## sub1: (num) energy sub-metering No. 1 (in watt-hour of active energy). It corresponds to the kitchen, containing mainly a dishwasher, an oven and a microwave (hot plates are not electric but gas powered).
## sub2: (num) energy sub-metering No. 2 (in watt-hour of active energy). It corresponds to the laundry room, containing a washing-machine, a tumble-drier, a refrigerator and a light.
## sub3: (num) energy sub-metering No. 3 (in watt-hour of active energy). It corresponds to an electric water-heater and an air-conditioner.


## Step #6 - Create the plot - In this case a Histogram
hist(newdataset$activepwr, col = "red", main="Global Active Power", xlab="Global Active Power (kilowatts)", ylab= "Frequency")

## Step #7 - Save the plot to a PNG file with a width of 480 pixels and a height of 480 pixels.
dev.copy(png, file="plot1.png", width = 480, height = 480) # Copy my plot to a PNG file 
dev.off() ## Closing the PNG device
