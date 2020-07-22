---
title: "A Scarred Generation"
subtitle: "Analysis of School Shootings in the United States"
layout: post
date: 2019-04-29 13:00
headerImage: false
tag:
- R
- STA199
projects: true
category: project
author: meredithbrown
description: "Final project for Statistics 199, taken Spring 2019."
--- 

## Introduction

*A Scarred Generation* was my [final team project](https://www2.stat.duke.edu/courses/Spring19/sta199.001/project/project.html
) for [STA199: Introduction to Data Science](https://www2.stat.duke.edu/courses/Spring19/sta199.001/). I worked with [Sam Morin](https://github.com/morinsb), [Cindy Weng](https://github.com/wengcindy), and [Rodrigo Araujo](https://github.com/RodrigoAra) to formulate an interesting research question, collect, clean, and analyze relevant data, and present our findings to our professor, teaching assistants, and peers.

This project focused on the analysis of data from the Washington Post’s GitHub detailing school shootings in the United States. Each observation is from a shooting that took place before, during, or immediately after school classes, and each observation is a single shooting. Before analysis, the data filtered out observations in the dataset that were committed by security guards of any kind, as these were instances where a guard retaliated against someone with a gun. Further, for deeper analysis, data about states was analyzed to provide information about the kinds of environments in which these shootings are occurring. All of this information was used to answer the question: What features of people and communities characterize high casualty school shootings?

## Presentation

From a dataset of 213 observations and 50 variables, we decided to tackle this question by exploring four main areas of data: state data, socioeconomic status of the targeted schools, physical characteristics of the shooter, and the weapons used. These initial areas of exploration were then aggregated into a full model, on which backwards selection via AIC was performed.

```r
## # A tibble: 9 x 2
##   term                           estimate
##   <chr>                             <dbl>
## 1 (Intercept)                  -26.0     
## 2 age_shooter1                   0.453   
## 3 prop_lunch                    -7.02    
## 4 weapon_typenon-semiautomatic   3.36    
## 5 weapon_typesemiautomatic       5.84    
## 6 num_weaponsmultiple            5.34    
## 7 ownership_rate                 0.239   
## 8 density                        0.0113  
## 9 per_capita_income              0.000277
```

<iframe src="../assets/projects/a_scarred_generation/Stat199_Final_Project.pdf" style="width:600px; height:350px;" frameborder="0"></iframe>

## Conclusion and Discussion

This project sought to answer the question: What features of people and communities characterize high casualty school shootings? In doing this, we divided our analysis into four main sections: socioeconomic status, state data, physical traits, and weapons. Socioeconomic status included analyzing the proportion of students enrolled in schools where shootings occurred that qualify for free/reduced lunch. Using a linear model to predict number of casualties from this proportion, it was found that schools with higher proportion of students who qualify for free/reduced lunch tend to have had lower casualty rates. This was confirmed by a 95% confidence interval for the slope of the relationship between proportion free/reduced lunch and casualties, as the confidence interval was entirely below 0, implying a negative correlation between an increased proportion of free/reduced lunch and and casualties.

Further, state data was analyzed for macro-level impacts on school shootings. For this analysis, five variables were analyzed: density, depressive rates, weekly religious attendance rates, gun ownership rates and per capita income. The relationship between each of these variables and the number of state shooting events per one million people was graphed using linear models. Backwards selection was used on a full model with all of these variables to predict which variables most affect the number of shootings. It was found that religious attendance rates, contrary to our initial thoughts, was the most predictive of number of shootings.

After looking at these high level trends, we then explored the physical traits of shooters. To look at the trends, graphs of the relationship between total casualties and race, total shootings and race, and shooting types by race were produced. These graphs showed that black shooters committed more targeted shootings, as their casualty value was more proportional, whereas white shooters committed more indiscriminate shootings, as their casualty value was significantly higher. These findings were confirmed by the third graph. Further, using a full model predicting casualties from age, race, and gender of the shooter, it was found that gender was not significant as a predictive factor, as almost all the shooters were male. The best model, then, for predicting number of casualties from physical traits is based on age and race of the shooter.

Finally, the type of weapon and number of weapons used in the shootings were analyzed to look for patterns. Both of the variables were created by mutating the given weapons variable, and then a linear model to predict casualties from these variables was created. It was found that the use of a semiautomatic weapon and the use of multiple weapons significantly increased the number of casualties. For further analysis, a plot of the types of shootings committed with the types of weapons was created. This showed semi-automatic weapons have a higher proportion of accidental shootings, and when the weapon is missing after the fact, there is a higher proportion of targeted shootings.

To put all of this together, a full model was used to predict which of the variables produced throughout our analysis were most significant in predicting a high number of casualties. In starting from a full model and using backward selection, the best model showed that the most significant variables to the number of casualties a school shooter can cause were age, socio-economic status of the school, number and type of weapons used, and gun ownership rate of that state. Thus, these are the features of people and communities that most specifically characterize high casualty school shootings.

In this analysis, we frequently used linear models to highlight relationships between casualties and various variables. However, these linear models were often contained within different sections and rarely accounted for the interaction of the variables. Thus, to improve this analysis, a section could be added to look at the interaction between things such as socioeconomic status and race or race and gun ownership states. These interactions could then be included in the full model to produce a more complete analysis. However, the methods used in this analysis and the data on which they were used were valid and appropriate for coming to this conclusion, as our conclusion echos conclusion come to by experts in the field of gun violence.

Likewise, if this project were to be repeated, it could be interesting to compare what we have found here about school shootings in the United States to shootings in different countries that have similar statistics, such as similar religious attendance rates, gun ownership rates, or racial make-ups. This could provide compelling evidence for how the United States’ gun policies potentially influence the rate of school shootings and the resulting high numbers of casualties.