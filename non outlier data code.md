x1 = data1\$V1 y1 = data1\$V2 plot(x1, y1, xlab = x.lab, ylab = y.lab)
tsdata1 \<- ts(data1\$V2, frequency = 365, start = c(2023, 1))
plot(tsdata1) autoarima2 \<- auto.arima(tsdata1) auto.arima(tsdata1)
forecast2 \<- forecast(autoarima2, h = 91) forecast2 plot(forecast2)
plot(forecast2\$residuals) qqnorm(forecast2\$residuals)
acf(forecast2\$residuals) pacf(forecast2\$residuals) df1 \<- data1 inv1
\<- InvBoxCox(forecast2\$residuals, BoxCox.lambda(df1))
autoplot(tsdata1) + autolayer(inv1)
