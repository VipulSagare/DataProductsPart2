---
title       : Reproducible Pitch Deck
subtitle    :    for Developing Data Products Project
author      : Vipul Sagare
job         : for this projects-student
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

##  Reproducible Pitch



- This peer assessed assignment has two parts. First, you will create a Shiny application and deploy it on Rstudios servers. Second, you will use Slidify or Rstudio Presenter to prepare a reproducible pitch presentation about your application.

- HEre is the code and details:  "https://github.com/VipulSagare/DataProductsPart1"

-  Here are the project requiremnt: "https://class.coursera.org/devdataprod-015/human_grading/view/courses/973542/assessments/5/submissions"

---

## mtcars dataset

### Motor Trend Car Road Tests

> The data was extracted from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles (1973-74 models).
### Source
> Henderson and Velleman (1981), Building multiple regression models interactively. Biometrics, 37, 391-411.

```r
library(datasets)
head(mtcars, 2)
```

```
##               mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4      21   6  160 110  3.9 2.620 16.46  0  1    4    4
## Mazda RX4 Wag  21   6  160 110  3.9 2.875 17.02  0  1    4    4
```

---

## mtcars dataset - Format

**A data frame with 32 observations on 11 variables.**

| Index | Field | Detail |
------- | ----- | ------ |
| [, 1] | mpg | Miles/(US) gallon |
| [, 2]  | cyl | Number of cylinders |
| [, 3]  | disp | Displacement (cu.in.) |
| [, 4]	| hp | Gross horsepower |
| [, 5]	| drat | Rear axle ratio |
| [, 6]	| wt | Weight (lb/1000) |
| [, 7]	| qsec | 1/4 mile time |
| [, 8]	| vs | V/S |
| [, 9]	| am | Transmission (0 = automatic, 1 = manual) |
| [,10]	| gear | Number of forward gears |
| [,11]	| carb | Number of carburetors |

---

## Analysis - main code

```r
  formulaTextPoint <- reactive({
    paste("mpg ~", "as.integer(", input$variable, ")")  })
  
  fit <- reactive({
    lm(as.formula(formulaTextPoint()), data=mpgData)  })
  ...
  output$fit <- renderPrint({
    summary(fit()) })
  
  output$mpgPlot <- renderPlot({
    with(mpgData, {
      plot(as.formula(formulaTextPoint()))
      abline(fit(), col=2)
    })  })

```
## The END 
