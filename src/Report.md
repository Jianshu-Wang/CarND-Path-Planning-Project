# CarND-Path-Planning-Project Report
Self-Driving Car Engineer Nanodegree Program

### Reflection
In this section, I am going to describe how I managed to pass each rubic point. I have tested the code and the car is able to drive more than 10 miles without incidents. 

### Decision make by using sensor fusion data
The path generation model follows the project walkthrough by Udacity. The following steps are applied (all line references in relationship to main.cpp):

* First, we examine all data from sensor fusion, we then make decision based on their location and make prediction of those cars, those may be changing their lane, so we need to calculate their velocity of d and is make sure if they are changing lane. 

* If there is a car in front of us, and close to us, we first need to consider to change the lane. 

* Now we need to make sure it is safe for us to change the lane, and we need to distinguish to change to the right/left lane.   

* If safe, we start to make a good spline line and to drive the car to follow it. 

* If not safe we must keep in the lane and to take action by distinguishing if our velocity to higher then the car ahead. 

* If our velocity is higher, and within a dangerous distance, then we slow down. 

* If we dont have car ahead within a dangerous distance, then we speed up if we are under the target velocity. 


### Trajectory Generation

* The first control points are the last two points from the remaining path returned by the simulator. 

* if no points in the previous path, then we use the current point of the car. 

* Then spline points are transformed to vehicle coordinates. points are sampled up to 30m, number of points that are sampled is determined by the reference velocity.


### Speed Limit

* Check if we want to change the lane or slow down. 

* If no, then check it the speed is smaller than 49.5. 

* If yes, then increase the my reference speed by 0.3. 


### Acceleration and Jerk

* When speed up we only add 0.3 to the current reference speed, and update it, that give a limitation of acceleration

* When slow down, we abstract 0.3 to the current speed, and update it. 

### Collision

* Because we did prediction of cars' behavior so we can avoid collision. 

* And we also dont change lane when our speed to slower than the car behind who is within a dangerous range. 





