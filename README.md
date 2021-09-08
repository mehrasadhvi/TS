<snippet>
  <content><![CDATA[
# ${1:Anomaly Detection}

The given sytem detects whether their are anomalies in a given univariate time series data.It deducts outliers and estimate anomalies by building a model and checking how far
new point lies from the original line ; as it is ts data there may be some trend as well as periodicity, firstly we extract these components then see the confidence region.
The point outside this region is anomaly

## Libraries

The libraries  used are pandas,numpy,matplotlib,statsmodel

## Data
 The data used is a univariate time series of cloud bills(2435 observations) recorded over a period of 7 years.The data set does not contain any null values.(The path specified can be changed accordingly)

## Anomaly Detection

A function named anomaly_det is defined which takes in any  dataset as an argument;Proceeding for anomalies it further drops out the rows with NAN value.
A boxplot with a predefined size is plotted to visualise the outliers (an observation that lies an abnormal distance from other values in a random sample from a population)
Inter  Quartile Range is computed so as to recognize an outlier(Any observations that are more than 1.5 IQR below Q1 or more than 1.5 IQR above Q3 are considered outliers)
The given function works under an underlying assumption that any dataset will contain timestamp,date in 1st column and Timeseries recorded in the 2nd column.Based on this assumption the Outliers are appended in a list while iteration.
The Date column is then converted to index column,since while decomposing a time series into deterministic components only integral parameter is accepted.
As every real time series data has some trend and periodicity,the individual components are extracted.And an estimated model is plotted with original to visualise the contrast.
The difference of the two models is residuals,when the residual has an extremely large value as compared to the others it might qualify as an anomaly
The 99% confidence interval is computed (mu-3SD,mu+3SD).this method works better than outlier detection for time series.Any point lying outside
 is an anomaly which is stored further in a list
In case any data which contains null values,or exhibit any of the foregoing behaviour is considered anamolous.(The path and data can be changed accordingly)
