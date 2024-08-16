tsdata \<- ts(data\$Reach, frequency = 365, start = c(2023, 1))
plot(tsdata) autoarima1 \<- auto.arima(tsdata) auto.arima(tsdata)
forecast1 \<- forecast(autoarima1, h = 91) forecast1 plot(forecast1)
plot(forecast1\$residuals) qqnorm(forecast1\$residuals)
acf(forecast1\$residuals) pacf(forecast1\$residuals) library(forecast)
library(ggfortify) inv \<- InvBoxCox(forecast1\$residuals,
BoxCox.lambda(df)) autoplot(tsdata) + autolayer(inv)
