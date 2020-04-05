# F1 Fantasy 2020

### Table of Contents: 
* [Basics of Formula 1](#Basics-of-Formula-1)
* [F1 Fantasy Rules](#F1-Fantasy-Rules)
* [F1 Fantasy Points](#F1-Fantasy-Points)
* [Optimization Formulation](#Optimization-Formulation)

## Basics of Formula 1:
In case you are new to F1 like myself -- having only watched the [Netflix series](https://www.netflix.com/title/80204890) -- F1 is has a relatively small field for each race. Qualifying occurs in a three-stage "knockout" system. During stages all drivers who have not yet been eleminated are on the track try to set the fastest lap time. This process sets the starting grid for the race which is typically held on Sunday. 

Each team a.k.a constructor has two race car drivers. The top 10 drivers in Sunday's race score points (25,18,15,12,10,8,6,4,2,1) plus the driver who has the fastest lap gets 1 point. For example, if the two Mercedes drivers (Lewis Hamilton & Valtteri Bottas) place first and third plus Bottas has the fastest lap then Mercedes scores 25 + 15 + 1 = 41 points in pursuit of the **Constructors World Championship**. But Hamilton would have scored 25 - 16 = 9 points more than Bottas in pursuit of the **Drivers World Championship**. Hence teammate rivalries can be fierce in F1. 

Fantasy points are a little more complex which is detailed in a later section. A few preliminary questions I had when watching...  

**Question:** How does a driver's start position affect his finish position? 

<p align="center">
  <img src="imgs/2018_ResultvStart.png" width="400"/>
  <img src="imgs/2019_ResultvStart.png" width="400"/>
</p>

**Question:** Since only the top 10 drivers score, are drivers that start outside top 10 less likely to finish? (NC = Not Classified, DQ = Disqualification)

<p align="center">
  <img src="imgs/2018_NCs.png" width="400"/>
  <img src="imgs/2019_NCs.png" width="400"/>
</p>


## F1 Fantasy Rules:
<p align="center">
  <img src="imgs/Select_Team.png" width="400"/>
</p>

1) Pick a team of 5 drivers and 1 constructor from a $100m budget. 
2) You must also select a Turbo Driver for each race who will score double points.
3) Only drivers priced at under $20m can be selected as your Turbo Driver.

Extra: 

* There are no restrictions on how many drivers can be used from a particular team.
* Turbo driver can be different for each race, but must be selected prior to saving your team and doesn't count as a substitution. If your Turbo Driver's price increases to above $20m after you have selected them as your Turbo Driver you can keep them as your Turbo Driver.
* You also have two Mega Driver plays per season which multiplies the points scored by the selected driver by 3x. 

For the details see [fantasy rules](https://fantasy.formula1.com/game-rules).

## F1 Fantasy Points:
The fantasy points system is complex. Each race your 5 **Drivers** and 1 **Constructor** score points during qualifying session and Sunday's race. **Constructor** points are usually calculated by adding together their two driver's points. Streak points are also give out for consistent performance across 3 and/or 5 races in a row.

For the details see [fantasy points](https://fantasy.formula1.com/points-scoring). 

## Optimization Formulation:
* The goal is to maximize the weekly total number of points of our team. 
* For all **Drivers** and **Constructors** we assign a binary decision of selected (X_s = 1) or not selected (X_s = 0). 
* Selected **Drivers** eligible for Turbo upgrade we assign a binary decision of selected (T_i = 1) or not selected (T_s = 0).  
<p align="center">
  <img src="imgs/MIP.png" width="500"/>
</p>

## Overview:
* Webscrape historical result data (qualifying, starting grid, race results) from [F1 website](https://www.formula1.com/en/results.html).   
* Calculate driver/constructor points based on [fantasy points scoring](https://fantasy.formula1.com/points-scoring).
* Apply [mixed integer programming (MIP)](https://developers.google.com/optimization/mip/integer_opt) to choose 2020 team based on 2019 points.
