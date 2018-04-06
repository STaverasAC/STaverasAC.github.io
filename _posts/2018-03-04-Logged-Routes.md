---
layout: post
title: Using analysis to inform decision about OPT Mobile App pilot launch. 
---

## Problem: OPT Mobile App is dependent on bus drivers logging stop events as they happen.

The Office of Pupil Transportation is developing a mobile application to inform guardians of the location of their child's bus and the estimated arrival time of that bus to their pick up and drop off location. In order to provide guardians with ETAs, it is necessary for drivers to log ridership events such as arrival and departure from stops as they happen. The routes selected for the pilot in June need to be served by drivers who will log ridership correctly.

## Solution: Script found [here](https://github.com/STaverasDev/GPSAnalysis/blob/master/LoggedStops.py).

Given that ridership data and GPS data exists as separate entities unaware of one another, I developed a script to determine if arrival events were being logged at the locations of student and school stops.The script iterates through each route performed on the given day and creates a subset of the schools, students andd gps points pertaining to that route. Buffers are created at 275 ft around students and 350 around schools.If a GPS point logged by the driver as an "Arrival" point falls within a buffer, that stop is considered to be logged correctly. For each route, the percentage of correctly logged stops is calculated.

#### Inputs

- Student location feature class
- School location feature class
- GPS data feature class

#### Outputs

CSV with following fields:
- Driver
- Route
- PCT of logged events

<img align="right" src="http://www.fillmurray.com/100/100">

![Image of Map](/images/FindGoodRoutesSmall.png)


## Answer

After merging the outputs of a month's worth of routes,it was possible to determine which drivers were logging events as they occured most frequently. 


