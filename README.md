legalanalyticsfinalcode
=======================
> stocks <- read.csv("data_akbilgic.csv")
> head(stocks)
       date          ISE        ISE.1           SP          DAX         FTSE       NIKKEI
1  5-Jan-09  0.035753708  0.038376187 -0.004679315  0.002193419  0.003894376  0.000000000
2  6-Jan-09  0.025425873  0.031812743  0.007786738  0.008455341  0.012865611  0.004162452
3  7-Jan-09 -0.028861730 -0.026352966 -0.030469134 -0.017833062 -0.028734593  0.017292932
4  8-Jan-09 -0.062208079 -0.084715902  0.003391364 -0.011726277 -0.000465999 -0.040061309
5  9-Jan-09  0.009859905  0.009658112 -0.021533208 -0.019872754 -0.012709717 -0.004473502
6 12-Jan-09 -0.029191028 -0.042361155 -0.022822626 -0.013525735 -0.005025533 -0.049038532
      BOVESPA           EU           EM
1  0.03119023  0.012698039  0.028524462
2  0.01891958  0.011340652  0.008772644
3 -0.03589858 -0.017072795 -0.020015412
4  0.02828315 -0.005560959 -0.019423778
5 -0.00976388 -0.010988634 -0.007802212
6 -0.05384947 -0.012451259 -0.022629745
> spm(~ISE.1 + SP + DAX + FTSE + NIKKEI + BOVESPA + EU + EM , data=stocks)
> m1 <- lm(ISE.1 ~ SP + DAX + FTSE + NIKKEI + BOVESPA + EU + EM, data=stocks)
> summary(m1)

Call:
lm(formula = ISE.1 ~ SP + DAX + FTSE + NIKKEI + BOVESPA + EU + 
    EM, data = stocks)

Residuals:
      Min        1Q    Median        3Q       Max 
-0.054156 -0.007969  0.000542  0.007853  0.051871 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.0005485  0.0005963   0.920 0.358106    
SP           0.0548698  0.0705293   0.778 0.436934    
DAX         -0.2126757  0.1204698  -1.765 0.078077 .  
FTSE        -0.2059296  0.1520761  -1.354 0.176277    
NIKKEI       0.0408475  0.0511000   0.799 0.424439    
BOVESPA     -0.2440132  0.0665978  -3.664 0.000273 ***
EU           1.0917300  0.2141996   5.097 4.82e-07 ***
EM           0.9923386  0.1126628   8.808  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.01371 on 528 degrees of freedom
Multiple R-squared:  0.5843,	Adjusted R-squared:  0.5788 
F-statistic:   106 on 7 and 528 DF,  p-value: < 2.2e-16
> m2 <- lm(ISE.1 ~ DAX + FTSE + NIKKEI + BOVESPA + EU + EM, data=stocks)
> summary(m2)

Call:
lm(formula = ISE.1 ~ DAX + FTSE + NIKKEI + BOVESPA + EU + EM, 
    data = stocks)

Residuals:
      Min        1Q    Median        3Q       Max 
-0.054798 -0.007957  0.000362  0.007859  0.052032 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.0005545  0.0005960   0.930 0.352660    
DAX         -0.1949370  0.1182482  -1.649 0.099835 .  
FTSE        -0.1993698  0.1517855  -1.313 0.189585    
NIKKEI       0.0418392  0.0510651   0.819 0.412967    
BOVESPA     -0.2163260  0.0562702  -3.844 0.000136 ***
EU           1.0961353  0.2140448   5.121 4.26e-07 ***
EM           0.9761992  0.1106950   8.819  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.0137 on 529 degrees of freedom
Multiple R-squared:  0.5838,	Adjusted R-squared:  0.5791 
F-statistic: 123.7 on 6 and 529 DF,  p-value: < 2.2e-16
> m3 <- lm(ISE.1 ~ DAX + FTSE + BOVESPA + EU + EM, data=stocks)
> summary(m3)

Call:
lm(formula = ISE.1 ~ DAX + FTSE + BOVESPA + EU + EM, data = stocks)

Residuals:
      Min        1Q    Median        3Q       Max 
-0.055041 -0.007992  0.000412  0.008343  0.051398 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.0005354  0.0005954   0.899   0.3689    
DAX         -0.1966380  0.1181933  -1.664   0.0968 .  
FTSE        -0.2089375  0.1512887  -1.381   0.1678    
BOVESPA     -0.2302949  0.0536086  -4.296 2.07e-05 ***
EU           1.1005042  0.2139120   5.145 3.78e-07 ***
EM           1.0286207  0.0903038  11.391  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.0137 on 530 degrees of freedom
Multiple R-squared:  0.5833,	Adjusted R-squared:  0.5793 
F-statistic: 148.4 on 5 and 530 DF,  p-value: < 2.2e-16
> m4 <- lm(ISE.1 ~ DAX + BOVESPA + EU + EM, data=stocks)
> summary(m4)

Call:
lm(formula = ISE.1 ~ DAX + BOVESPA + EU + EM, data = stocks)

Residuals:
      Min        1Q    Median        3Q       Max 
-0.055814 -0.007854  0.000290  0.008038  0.052443 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.0005149  0.0005957   0.864    0.388    
DAX         -0.1653683  0.1161034  -1.424    0.155    
BOVESPA     -0.2315351  0.0536468  -4.316 1.90e-05 ***
EU           0.8769010  0.1399198   6.267 7.61e-10 ***
EM           1.0261241  0.0903628  11.356  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.01371 on 531 degrees of freedom
Multiple R-squared:  0.5818,	Adjusted R-squared:  0.5786 
F-statistic: 184.7 on 4 and 531 DF,  p-value: < 2.2e-16

> m5 <- lm(ISE.1 ~ BOVESPA + EU + EM, data=stocks)
> summary(m5)

Call:
lm(formula = ISE.1 ~ BOVESPA + EU + EM, data = stocks)

Residuals:
      Min        1Q    Median        3Q       Max 
-0.054666 -0.007918  0.000285  0.007882  0.051979 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.0004758  0.0005956   0.799    0.425    
BOVESPA     -0.2335540  0.0536799  -4.351 1.63e-05 ***
EU           0.7024443  0.0677052  10.375  < 2e-16 ***
EM           1.0303495  0.0904013  11.398  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.01372 on 532 degrees of freedom
Multiple R-squared:  0.5802,	Adjusted R-squared:  0.5778 
F-statistic: 245.1 on 3 and 532 DF,  p-value: < 2.2e-16
> vif(m5)
 BOVESPA       EU       EM 
2.030383 2.196984 2.559685 
> bptest(m5)

	studentized Breusch-Pagan test

data:  m5
BP = 8.292, df = 3, p-value = 0.04035
