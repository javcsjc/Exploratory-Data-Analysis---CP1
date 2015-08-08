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


## Process Overview

* Step #1 - Read data from household_power_consumption.txt file
* Step #2 - Select the subsets that match the dates "1/2/2007" and "2/2/2007"
* Step #3 - Create a new variable "fulldatetime" that combines Date and Time.
* Step #4 - The resulting variable type for "fulldatetime" was (chr). We need to change to "POSIXlt"
* Step #5 - Rename columns of the dataset and change their order, so the new variable "fulldatetime" appears right after Date & Time.
* Step #6 - Create plot(s)
* Step #7 - Save the plot(s) to a PNG file with Width = 480 and Height = 480. Making sure to close the PNG device.

## Variable names and order of new data set:
* date: (chr) Date in format dd/mm/yyyy
* time: (chr) Time in format hh:mm:ss
* fulldatetime: (POSIXlt) Date and time in the format yyyy-mm-dd hh:mm:ss
* activepwr: (num) household global minute-averaged active power (in kilowatt)
* reactivepwr: (num) household global minute-averaged reactive power (in kilowatt)
* voltage: (num) minute-averaged voltage (in volt)
* intensity: (num) household global minute-averaged current intensity (in ampere)
* sub1: (num) energy sub-metering No. 1 (in watt-hour of active energy). It corresponds to the kitchen, containing mainly a dishwasher, an oven and a microwave (hot plates are not electric but gas powered).
* sub2: (num) energy sub-metering No. 2 (in watt-hour of active energy). It corresponds to the laundry room, containing a washing-machine, a tumble-drier, a refrigerator and a light.
* sub3: (num) energy sub-metering No. 3 (in watt-hour of active energy). It corresponds to an electric water-heater and an air-conditioner.

