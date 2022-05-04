# Henry Guan    
# 2022-01-25 -- Formation of Team, RFA, Initial Parts List
- Found group members to form a team, worked on the RFA, as well as formulating a basic parts list with teammates.  
# 2022-01-27 -- Initial RFA Post 
- Completed RFA with teammates and posted to Web Board for approval. RFA was rejected; took TA feedback into account and made revisions to the RFA accordingly. 
# 2022-02-01 -- Discussion with Dean Biskup (TA) 
- Discussed how we can get our project approved with Dean after the third class meeting. Made more revisions to RFA and posted it to the Web Board.  
# 2022-02-07 -- Project Proposal 
- Worked on the proposal with my teammates, creating the block diagram, problem statement, and the RV Tables.
# 2022-02-08 -- Github Repository 
- Created Github repository with my teammates, uploaded initial project files.
# 2022-02-09 -- Project Proposal 
- Completed remaining sections of the proposal and proofread everything afterwards.
# 2022-02-16 -- Design Document 
- Worked on the Design Document, revising the block diagram and the Requirements and Verification, and added more to the Introduction section. 
# 2022-02-21 -- Design Document Check 
- Had our design document check with Professor Schuh before our final design submission and design review. 
# 2022-02-23 -- Design Document 
- Took Professor Schuh's feedback into account and edited the different units, adding to the Requirements and Verification, as well as revising the block diagram and changing our scale to a load cell.  
- Helping out with figuring the circuit schematic with our MCU in our Control Subsystem. 
<p align="center">
<img src = "https://cdn.discordapp.com/attachments/903401697957789716/971307479701000222/blockdia.drawio.png">
</p>
<p align = "center">
<strong> Block Diagram </strong>
</p>

# 2022-02-28 -- Design Review 
- Thought about how the Design Review will go, delegating parts to each teammate for what to talk about, as well as how to address the different kinds of questions we can expect. 
# 2022-03-01 -- PCB Design & Reviews
- Met with my teammates to finalize our PCB footprint design, and incorporated feedback from the PCB Reviews with a TA.
# 2022-03-10 -- Machine Shop Design 
- Met with my teammates to revise machine shop design from the initial conversation. 
  - Agreed to downsize machine 
  - Modified dispensing mechanism from retracting mechanical arms to a conveyor belt
  
- Measured dimensions of our intended container of use, sketching and designing our new machine shop design around the container's dimensions.
<p align="center">
<img src = "https://cdn.discordapp.com/attachments/903401697957789716/971307463741698079/Machine_Shop_Contraption_G2G.png">
</p>
<p align = "center">
<strong> Physical Design Used for our Machine Shop Contraption </strong>
</p>

# 2022-03-11 -- Machine Shop & Parts
- Met with Gregg Bennett and Skee Aldrich to discuss our revised physical design and get it built. 
- Bought parts from the ECE Supply Center, specifically two servo motors (one continuous, one non-continuous), a demultiplexer, an ATMega328P, and LED diodes.  
# 2022-03-12 -- PCB Order
- Teammates and I agreed to independently order the PCB, as the first round deadline already passed by. 
# 2022-03-17 and 2022-03-21 -- Machine Shop 
- Met with Gregg Bennett to look at initial physical apparatus and left parts with Gregg to continue the build progress. 
# 2022-03-26 -- PCB Testing & PCB Revisions 
- All met up at the lab to complete PCB assembly by soldering all components in, and started to test the PCB.  
- We made a big mistake with the PCB, as we had a lot of wrong parts, particularly resistors, as they were not the right value we initially thought we needed for our PCB to be functional. 
  - We modified our PCB footprint design accordingly, preparing for secound round PCB orders.
- Ordered barcode/QR scanner camera module.
# 2022-03-28 and 2022-03-29 -- Individual Progress Report
- Worked on individal progress report.  
# 2022-04-04 -- Initial Testing 
- Met with John to test motor functionality within our physical apparatus.
- Ordered new continuous servo motor as our original unit was dead on arrival (DOA). 
- Looked into magnetic stripe cards and how data is processed and sent through an MSR 123 USB reader. 
- https://www.tutorialspoint.com/arduino/arduino_dc_motor.htm -- Tried following this tutorial
- https://www.arduino.cc/reference/en/libraries/magstripe/ - Went through some of the libraries for magstripe card readers
# 2022-04-05 -- Machine Shop Revisions
- Met with Gregg Bennett to make modifications to our physical apparatus according to our initial testing from the previous day. 
# 2022-04-06 -- Load Cell
- Met with John to test load cell using our initial software code. Got the load cell to output force readings to our serial monitor in Arduino. 
- https://www.instructables.com/Arduino-Scale-With-5kg-Load-Cell-and-HX711-Amplifi/ -- Tried following this tutorial   
# 2022-04-11 -- Testing & Integration 
- Met with John to independently test push buttons, servo motors, and load cell working. Integrated all three components to work in conjunction with one another. 
- Ordered USB Host Shield to test card reader. 
- https://docs.arduino.cc/built-in-examples/digital/Button -- Tried following this tutorial
# 2022-04-12 -- Second Round PCBs Arrived 
- De-soldered parts from old PCB and began soldering and preliminary testing on second PCB.
- There were issues with power delivery as it was exceeding the intended 5V delivery, so we used a separate external blank PCB board with MOSFETs and capacitors to properly regulate voltage from the DC power supply. 
<p align="center">
<img src = "https://cdn.discordapp.com/attachments/903401697957789716/971313502084018286/IMG_5931.jpg">
<img src = "https://media.discordapp.net/attachments/903401697957789716/971320907064811520/pcb.jpg?width=334&height=676"> 
</p>
<p align = "center">
<strong> Voltage Regulator (top) Connected to PCB (bottom) </strong>
</p>


# 2022-04-15 -- Received New Continuous Servo Motor & QR Scanner Testing
- Met with John to test new continuous servo motor in conjunction with the load cell, non-continuous servo motor, and push buttons. 
- Tested out QR scanner. We had a lot of issues with the QR code being not read in as a valid code and figured out that we needed to use a static QR code, rather than a dynamic one. 
- https://docs.arduino.cc/tutorials/mkr-vidor-4000/VidorQrRecognition -- Tried following this tutorial
# 2022-04-16 -- Swap to MSR90 Card Reader
- We were struggling a lot with the MSR 123 card reader, as it was not even initializing as an HID device, so we switched to the MSR 90 card reader, and it was able to successfully read in UIN data from our iCards.
- Integrated the software side for each module and tested the machine as a whole. The software worked for dispensing as well as retrieving.
<p align = "center">
<img src = "https://cdn.discordapp.com/attachments/903401697957789716/971312833566486598/retrieve.gif">
<img src = "https://cdn.discordapp.com/attachments/903401697957789716/971312807532458034/dispense.gif">
</p>
<p align = "center">
<strong> RETRIEVAL (left) AND DISPENSAL (right) </strong>
</p>

# 2022-04-17 -- PCB Debugging 
- Attempted to integrate PCB with our software, but our PCB was not working. 
- Probed all the components on our board, and found there was a huge voltage drop across components that were on the right side of the board. 
- Determined this voltage drop to be caused by a corroded SMD voltage regulator, which restricted current a lot.
  - Cause of corrosion was due to using water-soluble flux when desoldering from our original PCB
# 2022-04-22 -- Mock Demo
- Conducted our Mock Demo with our TA (Akshat). Tidied up final apparatus and got ready for final demo. 









