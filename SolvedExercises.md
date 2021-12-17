---
title: "R for Data Science"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
library(tidyverse)
```

### Exercises

 Run ggplot(data = mpg) what do you see?
```{r}
ggplot(data = mpg)
##  We see an empty box area
```

 How many rows are in mtcars? How many columns?
 
 ```{r}
 dim(mpg)
 ## We can see there are 234 rows and 11 columns
 ```
 
 
 What does the drv variable describe? Read the help for ?mpg to find out.
 
 ```{r}
## Whether the car is front wheel drive or not. 
## f = front-wheel drive, r = rear wheel drive, 4 = 4wd
 ```
 
 
 
 
 Make a scatterplot of hwy vcs cyl.
 
 ```{r}
 ggplot(mpg)+
  geom_point(aes(x = cyl, y = hwy))
```

  What happens if you make a scatterplot of class vs drv. Why is the plot not useful?
  ```{r}
  ggplot(mpg)
  ## Because both variables are categorical variables
  ```
  
  What's gone wrong with this code? Why are the points not blue?
  ```{r}
  ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy, color = "blue"))
  ```
  
  It should read as follows
  ```{r}
  ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy), color = "blue")
  ```
  
  Which variables in mpg are categorical? Which variables are continuous? (Hint: type ?mpg to read the documentation for the dataset). How can you see this information when you run mpg?
  
  
### Categorical
- Model
- cyl
- Manufacturer
- trans
- drv
- fl
- class

### Continuous
- displ
- year
- cty
- hwy 

Map a continuous variable to color, size, and shape. How do these aesthetics behave differently for categorical vs. continuous variables?

```{r}
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy, colour = cty))
# ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, shape = cty)) This creates an error
ggplot(data = mpg) +
  geom_point(mapping = aes(x = displ, y = hwy, size = cty))
```


What happens if you map the same variable to multiple aesthetics?
```{r}
ggplot(data = mpg) +
  geom_point(mapping = aes(x = displ, y = hwy, colour = cty, size = cty))
```

What does the stroke aesthetic do? What shapes does it work with? (Hint: use ?geom_point)
```{r}
## Stroke controls the width of the border of certain shapes. Those shapes which have borders are the only ones that stroke can alter.
```


What happens if you map an aesthetic to something other than a variable name, like aes(colour = displ < 5)?
```{r}
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy, colour = displ < 5))
```

ggplot turns displ < 5 into a boolean (or dummy) variable on the fly and maps that T or F to the colour argument.