<h1 align="center"> John Kim (jaehank2) Worklog </h1>


* [Summary](#summary)
* [Week of 2022-01-24](#week-of-2022-01-24)  
* [Week of 2022-02-01](#week-of-2022-02-01)  
* [Week of 2022-02-07](#week-of-2022-02-07)  
* [Week of 2022-02-14](#week-of-2022-02-14)  
* [Week of 2022-02-21](#week-of-2022-02-21)  
* [Week of 2022-02-28](#week-of-2022-02-28)  
* [Week of 2022-03-07](#week-of-2022-03-07)  
* [Week of 2022-03-14](#week-of-2022-03-14)  
* [Week of 2022-03-21](#week-of-2022-03-21)  
* [Week of 2022-03-28](#week-of-2022-03-28)  
* [Week of 2022-04-04](#week-of-2022-04-04)  
* [Week of 2022-04-11](#week-of-2022-04-11)  
* [Week of 2022-04-18](#week-of-2022-04-18)  
* [Week of 2022-04-25](#week-of-2022-04-25)  
* [Week of 2022-05-02](#week-of-2022-05-02)  



## Summary
This is a notebook outlining the work and progress I made from the start of the project.

## Week of 2022-01-24
* **01/25 (Getting Started on the RFA)**:
  * <ins>Objectives</ins>: Get to know the team and familiarize with the problem statement that the team is trying to solve
  * <ins>Overview</ins>: Our team was trying to automate a currently existent service used at the U of I dining halls. However, I was not too familiar with the current system and thus had to search online for how exactly the Good2Go system was managed and what problems there were. I realized that the current system required students to first receive a physical token and find a dining hall employee to exchange it for a new take-out container. After identifying the problems, I started working on the RFA (request for approval) to get started on our project.


## Week of 2022-02-01
* **02/01 (RFA Submission and Starting on Proposal)**:
  * <ins>Objectives</ins>: Get the RFA approved and start working on the proposal
  * <ins>Overview</ins>: The initial RFA post got rejected mainly because our team was not specific about the subsystem requirements. My team and I had a discussion with a TA named Dean Biskup to identify what we were missing in the RFA. I had a general idea of what kind of modules we were going to need for the project such as a motor, ID verification method, UI interface, and power supply components, the specifics were missing out as to how to integrate the entire components. I started looking into the details of each subsystem and was able to design an abstract FSM (finite state machine) with specific modules such as the QR scanner, scale, two sets of motors, display and a card reader. Additionally, I started outlining the criterion of success for our project, which required:
    1. Storing the tokens digitally for each user
    2. Allowing exchange between not only tokens for new containers but also old containers for new containers  

## Week of 2022-02-07
* **02/07 (Complete and Submit Proposal)**:
  * <ins>Objectives</ins>: Complete the proposal for submission
  * <ins>Overview</ins>: Even after getting the RFA approved, the proposal required extra work from each member. I was responsible for the design as well as the tolerance analysis. Our project required a mechanism to dispense exactly one container upon a single request, and the design that I came up with was to have two mechanical arms retracting in a order shown in the image below to dispense a single container while reloading the other containers.
    
    <img src="/images/orig_dispense.png" width="700" height="300">


    The design for the retrieval system required the machine to parallelize the sensor validtion process with the control subsystem. This was to allow the machine to retrieve a returned container the moment it finished validating the container, and thus I made a design to have two mechanical arms attached beneath the scale to lift up upon a command from the microcontroller. The image below shows physical design of the retrieval system.
    
    <img src="/images/orig_retrieve.png" width="500" height="300">
    
    The tolerance analysis was done on the motors using the below equation. Since our project requried a safe and accurate control mechanism of the motors, it required measurements on the angular position as well as the RPM (rotation per minute) of the two motors we were planning on using. 
    
    <img src="../../images/motor_equation.png" width="900" height="200">

* **02/11 (PCB Discussion)**:
  * <ins>Objectives</ins>:
  * <ins>Overview</ins>:

## Week of 2022-02-14
* 02/16: design doc

## Week of 2022-02-21
* 02/21: design doc check
* 02/23: changes to dd
* 02/27: pcb parts

## Week of 2022-02-28
* 03/04: start on motor code

## Week of 2022-03-07
* 03/07: finish pseudocode
* 03/10: machine shop design

## Week of 2022-03-14
* 03/15: parts finalized
* 03/17: machine shop order placed

## Week of 2022-03-21
* 03/21: start on fsm software
* 03/26: pcb testing & revision

## Week of 2022-03-28
* 03/28: individual progress report
* 03/29: servo motor code
* 04/02: software start button
* 04/03: hardware for button and finish

## Week of 2022-04-04
* 04/04: Software non-contin servo complete
* 04/07: Software load cell
* 04/08: load cell
* 04/09: load cell finish and QR start

## Week of 2022-04-11
* 04/11: finish QR
* 04/12: card reader code start
* 04/13: fail and debug
* 04/14: different method
* 04/15: msr90
* 04/16: finish card reader
* 04/17: integrate

## Week of 2022-04-18
* 04/19: try lcd but use led
* 04/22: mock demo
* 04/23: debugging and led lights
* 04/24: enclosure

## Week of 2022-04-25
* 04/26: final demo
* 04/27: start ppt

## Week of 2022-05-02
* 05/03: final ppt presentation