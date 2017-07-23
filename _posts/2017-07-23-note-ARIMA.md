---
layout: post
title: "Some about ARIMA model"
date: 2017-07-23 10:28:06 -603
comments: true
---

Note for  time series analysis model autoregressive moving average(ARMA) or autoregressive integrated moving average (ARIMA)

1). Autocorrelation: also known as serial correlation, is the correlation of a signal with a delayed copy of itself as a function of delay, it is the 

similarity between observations as a function of the time lag between them. the Analysis of autocorrelation is a mathematical tool for finding repeating

patterns, such as the presence of a periodic signal obscured by noise, or identifying the missing fundamental frequency in a signal implied by its 

harmonic  frequencies.

({{ site.baseurl}}/images/Autocorrelation.png)

2). Partial autocorrelation (PACF): gives the partial correlation of a time series with its own lagged values, controlling for the values of the time series at all shorter lags. 

({{ site.baseurl}}/images/PACF.png)

Modeling approach:

1).Model identification: using plots of the autocorrelation and partial autocorrelation functions of the dependent time series to decide which autoregressive or moving average component should be used in the model

2).Parameter estimation using computation algorithms to arrive at coefficients that best fit the selected ARIMA model. The most common methods use maximum likelihood estimation or non-linear least-squares estimation.

3). Model checking by testing whether the estimated model conforms to the specifications of a stationary univariated process.








