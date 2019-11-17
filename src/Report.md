# CarND-Path-Planning-Project Report
Self-Driving Car Engineer Nanodegree Program

### Reflection
In this section, I am going to describe how I managed to pass each rubic point. I have tested the code and it can drive the car more than 10 miles without incidents. 

### Decision make by sensor fusion data
The path generation model follows the project walkthrough by Udacity. The following steps are applied (all line references in relationship to main.cpp):

*1. First, we examine all data from sensor fusion, we then make decision based on their location and make prediction of those cars, those may be changing their lane, so we need to calculate their velocity of d and is make sure if they are changing lane. 

*2. If there is a car in front of us, and close to us, we first need to consider to change the lane. 

*3. Now we need to make sure it is safe for us to change the lane, and we need to distinguish to change to the right/left lane.   

*4. If safe, we start to make a good spline line and to drive the car to follow it. 

*5. If not safe we must keep in the lane and to take action by distinguishing if our velocity to higher then the car ahead. 

*6. If our velocity is higher, and within a dangerous distance, then we slow down. 

*7. If we dont have car ahead within a dangerous distance, then we speed up if we are under the target velocity. 


### Trajectory Generation

*1. The first control points are the last two points from the remaining path returned by the simulator. 

*2. if no points in the previous path, then we use the current point of the car. 

*3. Then spline points are transformed to vehicle coordinates. points are sampled up to 30m, number of points that are sampled is determined by the reference velocity.


### Speed Limit

*1. Check if we want to change the lane or slow down. 

*2. If no, then check it the speed is smaller than 49.5. 

*3. If yes, then increase the my reference speed by 0.3. 


### Acceleration and Jerk

*1. When speed up we only add 0.3 to the current reference speed, and update it, that give a limitation of acceleration

*2. When slow down, we abstract 0.3 to the current speed, and update it. 

### Collision

*1. Because we did prediction of cars' behavior so we can avoid collision. 

*2. And we also dont change lane when our speed to slower than the car behind who is within a dangerous range. 





