---
layout: post
title: Are school bus drivers logging events as they happen? 
---

## Question

The Office of Pupil Transportation is developing a mobile application to inform guardians of the location of their child's bus and the estimated arrival time of that bus to their pick up and drop off location. In order to provide guardians with ETAs, it is necessary for drivers to log ridership events such as arrival and departure from stops as they happen. Given that ridership data and GPS data exists as separate entities unaware of one another, I developed a script to determine if arrival events were being logged at locations of student and school stops.

## Solution

|Inputs|Output|
|---|---|
| <ul><li>Student location feature class</li><li>School location feature class</li><li>GPS data for 1 day</li></ul>|CSV with fields<ul><li>Driver</li><li>Route</li><li>PCT of logged events</li></ul>|

The python script found here, iterates through each route performed on the given day and creates a subset of the schools, students and gps points pertaining to that route. Buffers are created at 275 ft around students and 350 around schools. These distances were previously agreed on by analysts to determine whether a bus has arrived at a particular stop. If a GPS point logged by the driver as an "Arrival" point falls within a buffer, that stop is considered to be logged correctly. For each route, the percentage of correctly logged stops is calculated.

![Image of Map](/images/FindGoodRoutesSmall.png)

## Answer

After merging the outputs of a month's worth of routes,it was possible to determine which drivers were logging events as they occured most frequently. 


