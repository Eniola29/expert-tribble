# expert-tribble
```{r}
require(forecast)
require(fracdiff)
source("arma_innovation.R") #to source the arma innovation file
gas_dat <- read.csv("Gas Furnace Dataset.csv", header = TRUE)
head(gas_dat)
Output <- gas_dat[,2]
Input <- gas_dat$Input.gas.rate
```

#Use linear regression model - plot the ACF - what can you conclude ?
```{r }
gas_lm <- lm(Output ~ Input, data = gas_dat)
summary(gas_lm)
gas_residuals <-gas_lm$residuals
```


```{r pressure, echo=FALSE}
acf(gas_residuals, lag = 50)
```
