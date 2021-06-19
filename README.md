# Analyses-R-MultipleRegression
I was doing multiple regression analysis using R. Do you have any suggestions what else I can do with my analysis?


Background***
**The dataset was prepared by the Center of Spatial Data Science (CSDS). It includes data of the properties sold between May 2014 and May 2015. The data were sourced from the King County GIS Open Data.**

***Problem***
**In this analysis, I aimed to determine the best regression model that predicts the prices of properties that were purchased in King County in the state of Washington, USA. The word property refers to a collection of house and lot.**

***Methods***
#Load the packages. 
```{r, loading packages}
library(car)
library(psych)
library(readxl) #We need this package since the dataset is in Excel format. 
```

#Import the data to R. 

```{r, importing data}
dataset1 <- read_excel("dataset_housing.xlsx")
#This dataset is found in the working directory.
```
Below the an image of the list of variables. 
![image](https://user-images.githubusercontent.com/76488878/122652858-b6b11680-d106-11eb-97fb-93ef2b9f74d9.png)

#Run the multiple regression analysis. 

```{r, multiple regression1}
mreg1 <- lm(price ~ month_string + bedrooms + bathrooms + sqft_living + sqft_lot + 
             floors + waterfront_string + view + condition + grade + 
             sqft_above + sqft_basement + sqft_living15 + sqft_lot15, data = dataset1)
summary(mreg1)
```
*Notice that "sqft_basement" indicates NA. 

#Rerun the multiple regression, exclusing "sqft_living". 
```{r, multiple regression2}
mreg2 <- lm(price ~ month_string + bedrooms + bathrooms + sqft_lot + 
             floors + waterfront_string + view + condition + grade + 
             sqft_above + sqft_basement + sqft_living15 + sqft_lot15, data = dataset1)
summary(mreg2)
```
#Rerun the multiple regression, excluding "sqft_basement". 
```{r, multiple regression3}
mreg3 <- lm(price ~ month_string + bedrooms + bathrooms + sqft_living + sqft_lot + 
             floors + waterfront_string + view + condition + grade + 
             sqft_above + sqft_living15 + sqft_lot15, data = dataset1)
summary(mreg3)
```
