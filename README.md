# Forecasting-Project

# set working directory

setwd("C:/Míša")

# load libraries
library('vars')
library('ggplot2')
library('ggthemes')
library('reshape') 
library('readxl')
library('tseries')
library('na.tools')
library('grangers')
library('readr')

# load dataset
data <- read_csv("train.csv")

# keep only date and sales
# (we can also keep other variables if we want)
df <- subset(data, select = c(Date,Sales,Store))

# order by date
df <- df[order(as.Date(df$Date, format="%y-/%m-/%d")),]

# keep only store 1
df <- df[(df$Store == 1),]

# plots
plot(df$Date,df$Sales,type='l')
