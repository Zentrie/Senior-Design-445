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
* [References](#references)


## Summary
This is a notebook outlining the work and progress I made from the start of the project. All the references used are attached under the [References](#references) section at the very bottom.

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
  * <ins>Objectievs</ins>: Complete the proposal for submission
  * <ins>Overview</ins>: Even after getting the RFA approved, the proposal required extra work from each member. I was responsible for the design as well as the tolerance analysis. Our project required a mechanism to dispense exactly one container upon a single request, and the design that I came up with was to have two mechanical arms retracting in a order shown in the image below to dispense a single container while reloading the other containers.  
  &nbsp; &nbsp; <img src="/images/orig_dispense.png" width="700" height="300">

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The design for the retrieval system required the machine to parallelize the sensor validtion process with the control subsystem. This was  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; to allow the machine to retrieve a returned container the moment it finished validating the container, and thus I made a design to have  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; two mechanical arms attached beneath the scale to lift up upon a command from the microcontroller. The image below shows physical  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; design of the retrieval system.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/orig_retrieve.png" width="400" height="200">

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The tolerance analysis was done on the motors using the below equation. Since our project requried a safe and accurate control  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; mechanism of the motors, it required measurements on the angular position as well as the RPM (rotation per minute) of the two motors  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; we were planning on using. The motor used for the retrieval system needed a closed loop feedback system to be able to rotate properly  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; and the speed of the motor was controlled by sending different pulse data. 

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/motor_equation.png" width="600" height="150">

* **02/11 (PCB Discussion)**:
  * <ins>Objectives</ins>: Discuss the components of the PCB and general pin layout
  * <ins>Overview</ins>: The PCB required getting the footprints of each module our team was planning on using. This meant that we had to decide on the specific modules we were planning on using to get an idea of what kind of pin layouts the schematic would use. There was still some confusion between the exact components we needed, and thus I had worked on finalizing on what materials we needed. All the power and ground wires (VCC and GND) were ignored in the above consideration and only the digital and analog pins are discussed below. Regardless of the model number, the push buttons as well as the motors were going to have 1 data pin. The QR scanner was going to utilize a UART serial communication using the RX (receive) and TX (transmit) pins. The load cell had its own pin layout from the datasheet, but required an amplifier that essentially used serial clock and one data pin. The card reader was going to be connected to the microcontroller through a USB cable, and the power supply was going to utilize a voltage regulator to convert from 12V to 5V. Lastly the LEDs needed 6 to 7 pins, so using a mux was able to cut down the pin numbers to have 3. The below image shows the final schematic layout with the footprints.

<p align="center">
<img src="/images/pcb_schematic.png" width="250" height="400"> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/pcb_layout.png" width="300" height="300">
</p>

<p align="center">
 <strong>PCB Layout (Left), PCB Schematic (Right)</strong>
</p>

## Week of 2022-02-14
* **02/16 (Design Document)**:
  * <ins>Objectives</ins>: Finish writing design document for initial submission
  * <ins>Overview</ins>: This week, I mainly focused on writing several parts of the design document. Not only did I add more details for each subsystem and incorporate the design changes we made as a team, but also worked on the Requirements and Verification table. A lot of the requirements for the project required correct mechanical execution that heavily depended on the software code. Thus, some of the verification methods included utilizng the serial monitor for debugging purposes.

## Week of 2022-02-21
* **02/21 (Design Document Check)**:
  * <ins>Objectives</ins>: Check the initial design document submission with our TA
  * <ins>Overview</ins>: After the initial submission of our design document, we received feedback on both the writing requirements as well as the technical aspects. There were a few grammatical errors, but it was mostly about the entire structure of the paper. I revised the format of the document to follow the example paper given on the course website. Additionally, the tolerance analysis needed a bit more work as now I realized that the angular position required to go beyond 90 degrees regardless of the RPM to correctly retrieve the returned container.

* **02/23 (Changes to Design Document)**:
  * <ins>Objectives</ins>: Final submission of design document
  * <ins>Overview</ins>: Made the final changes outlined during the design document check and went over all the small writing details such as the TOC (table of contents) and paging rules. The block diagram also needed changes as we had to specify whether the type of data line was digital or analog. The power supply lines also need specifications as to what voltage it required (e.g. 12V or 5V or 3.3V). The below block diagram reflects the final changes made.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/block_diagram.png" width="500" height="300">

* **02/27 (PCB Parts)**:
  * <ins>Objectives</ins>: Finalize on PCB parts
  * <ins>Overview</ins>: After acquiring the footprints of each module for the PCB schematic, we had to order the right parts to actually connect to the PCB components. I went through a lot of design considerations such as between servo and stepper motors. In the end, I decided on certain parts like the continuous and non-continuous servo motors as well as acquiring a specific barcode/QR scanner from WaveShare.

## Week of 2022-02-28
* **03/04 (Software Motor Code)**:
  * <ins>Objectives</ins>: Start on writing the software code for motors
  * <ins>Overview</ins>: Because we were dealing with two different types of servo motors (continuous and non-continuous), they were operating in different modes and thus needed different code to run the two. As most of the parts were currently not available for actual testing because they were either still being shipped or being used by the machine shop for the physical design, I had written code for simply testing whether the motors were working or not. The two peices of code that I ran were based on position data and pulse data. This is when I realized we had a malfunctioning continuous motor as it wasn't even getting powered on. I notified my team members and ordered a new component.

## Week of 2022-03-07
* **03/07 (Finish Pseudocode)**:
  * <ins>Objectives</ins>: Finish Pseudocode for the entire project with all sensors
  * <ins>Overview</ins>: Even after getting the individual components working, integrating would add a lot of changes to the written code and so I decided to first work on the general state machine of the project. This way, all the code that I would write for each control and sensor module would take into account the type of input and output they need to be receiving and sending. The below image that I made shows the different state transitions. The initial state corresponds to the idle state of the machine waiting for a card swipe. Only then would the machine activate and start executing other exchange processes.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/FSM.png" width="500" height="300">

* **03/10 (Machine Shop Design)**:
  * <ins>Objectives</ins>: Provide design schematic for the machine shop
  * <ins>Overview</ins>: Since our project was creating a physical product without any basis to automate a currently existing service, there were complex design schematics we had to create to hand off to the machine shop. Only then would they be able to actually build what we had intended. I started looking into the specs of the different modules we bought as these were critical in determing the exact orientations and placements of the sensors. For example, the QR scanner required a specific tilt tolerance and limited FOV (field of view). Also since our machine had to be downscaled compared to what we had originally planned, we had to effectively make use of the space. The below diagram shows the design specifications my team and I made for the machine shop.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/design_spec.png" width="300" height="400">

## Week of 2022-03-14
* **03/15 (Finalizing on Parts)**:
  * <ins>Objectives</ins>: Finish ordering all parts required for the project
  * <ins>Overview</ins>: After buying all the big components of the project including the QR scanner, card reader, load cell, and motors, there were still a few other elements we needed. We had to buy different types of LEDs for the status messages as well as an amplifier as the load cell may give out weak signals that are hard to perform a digital read on.

* **03/17 (Machine Shop Order Check)**:
  * <ins>Objectives</ins>: Give all components needed to machine shop for completion of the physical design
  * <ins>Overview</ins>: Despite the design schematic with all specs labeled out, the machine shop required all components in hand to completely finish off the physical design. Thus the continuous motor that I had found defective had arrived this week, and needed to hand that off along with the LEDs to get our actual design finished. The below images show what our machine looked like right after the machine shop had finished making it.

<p align="center">
 <img src="/images/front_view.png" width="300" height="300">
 <img src="/images/topdown_view.png" width="300" height="300">
 <img src="/images/back_view.png" width="300" height="300">
</p>

<p align="center">
 <strong>Front View (Left), Top-down View (Center), Back View (Right)</strong>
</p>

## Week of 2022-03-21
* **03/21 (Software FSM Code)**:
  * <ins>Objectives</ins>: Finish the pseudocode for FSM
  * <ins>Overview</ins>: The individual modules still required their own code to actually work, but I made separate helper functions corresponding to different sensor modules. Thus whenenver the FSM required a certain execution of a module, I would call the appropriate functions (e.g. QRread()) that were at this point in time void functions without any lines of code. The FSM code was written first to get an idea of the logic flow and which tasks had higher priority compared to others.

* **03/26 (PCB Testing & Revision)**:
  * <ins>Objectives</ins>: Testing and revising the PCB order
  * <ins>Overview</ins>: I tried helping out with some of the PCB testings while mainly working on the software side. I realized that despite the individual software testing that I have been doing using Arudino uno and a USB host shield, the PCB had to achieve its full functionality as soon as possible to be incorporated into our project. I mainly helped out with soldering the parts and also probing each component to see if there were any faulty chips or wrong connections made within the board itself.

## Week of 2022-03-28
* **03/28 (Individual Progress Report):**
  * <ins>Objectives</ins>: Work on individual progress report for submission
  * <ins>Overview</ins>: I put a short pause on the software and pcb work to work on writing up my individual progress report. This report includes all the personal work I had done so far along with some of the software code I had written.

* **03/29 (Software Servo Motor Code)**:
  * <ins>Objectives</ins>: Finish the code for both continuous and non-continuous servo motors
  * <ins>Overview</ins>: Now that I had the initial code written for both the FSM and the motors, I worked on finishing up the codes for the motors to actually work with the intended design of our machine. The requirement was that the non-continuous motor that was responsible for the retrieval system required angular position data as well as the speed at which it rotates. Initially I had tried getting the motor to rotate slighly below 90 degrees with fast speed to "throw out" the returned containers but turned out to be a bit unsuccessful as it was getting too unsafe. The final testing gave a good result for rotating to 110 degrees witha delay of 10ms for each positional write. </br> </br> The continuous motor, on the other hand, had to go through some tuning process. Although sending a pulse of 1.5ms should have technically stopped the motor, it wasn't doing so and thus I used an adjustment screw and a potentiometer with PWM (pulse width modulation) to find the exact pulse for stopping. I also had to adjust the duration in which the continuous motor ran as it didn't have any closed loop feedback system. The below image shows the piece of code for the above behaviors. 

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/motor_code.png" width="300" height="300">

* **04/02 (Software Push Button Code)**:
  * <ins>Objectives</ins>: Software code for the two push buttons
  * <ins>Overview</ins>: The two push buttons that we were using for the project was slightly different than the normal push buttons with 4 legs. The push buttons that we had only had two legs and were operating in maintain-contact mode. This meant that the push button maintained whatever status it was before until another press was made. For example, the data pin for the push button will continuously read OFF (0) until a press is made at which the pin will now continuously read ON (1). The code was written such that it registers the initial button press and only measures the change in the states when needed. This method allowed other processes with higher priority such as the USB task and the UART communication to run without any delay.

* **04/03 (Hardware Push Button)**:
  * <ins>Objectives</ins>: Push Button Issue and Hardware
  * <ins>Overview</ins>: One problem with the push buttons was that the two legs had different types of wires, and needed extra soldering to fit into our PCB. I had notified my teammates about this and was able to get a small board layout to add different wires for the push buttons. The testing of the push buttons were done through a serial monitor to constantly check for the pressed state. However one major issue that I faced was that the buttons were left in a floating state and thus had to add a pull up resistor to define the logic states of the two buttons. The right image below shows the faulty behavior I got, and the left image shows the correct behavior of switching states upon a press.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/button_error.png" width="500" height="300">

## Week of 2022-04-04
* **04/04 (Software Motor Debugging)**:
  * <ins>Objectives</ins>: Non-continuous servo motor debugging
  * <ins>Overview</ins>: When running my software code on our actual machine, I started noticing a weird behavior of one of the motors that we were using when powered up. The normal executions of the motors were fine, but only in the beginning, the motor would shoot up to a 90 degree position when we required it to stay at 0 degrees until it received commands from the microcontroller. After doing some searching, I found out that the motors drew a lot of power and thus required a separate power supply. The solution that I came up with was to have another battery pack of 5V and also add a capacitor in the circuit. Lastly, I sent some initial data commands to the motors on start up to ensure no erratic behaviors were made.

* **04/07 (Software Load Cell Code)**:
  * <ins>Objectives</ins>: Software code for load cell
  * <ins>Overview</ins>: I started working on the software code for the load cell, and realized I had to go through some calibration process. Most scales already come with the calibration done, but the load cell itself had to be manually calibrated for accurate weight measurements. Since our machine had to weigh very light food containers, the below code was written with the use of an amplifier to adjust the calibration factor. The process included placing a known weight onto the load cell and constantly adjusting the calibration factor until the measurement was within a small margin of error.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/loadcell_init.png" width="500" height="300">

* **04/08 (Software Load Cell Code)**:
  * <ins>Objectives</ins>: Software code for load cell continued
  * <ins>Overview</ins>: After the initial calibration was completed, I started working on actual weight measurements within the software. Since the load cell was calibrated for reading small weights, even small small pressure onto it by human contact made extreme fluctations for the readings. Thus I had introduced some delay in the loadcell measurement to start reading weight data until the returned container was fully placed and succeeded in the QR scanning. I then averaged out the weight readings to get an accurate measurement.

* **04/09 (Software Load Cell Complete and Starting QR Code)**:
  * <ins>Objectives</ins>: Load cell wrap up and starting on software code for QR
  * <ins>Overview</ins>: The last part of the loadcell code required coming up with weight thresholds for the validation process. We required that the returned container shouldn't contain too much food waste. Thus if the container weighed more than 7g compared to its base weight, we would have to reject the container. I set a weight threshold of 10g as the base weight of the container turned out to be approximately 3g. The exact resolution of the loadcell directly links to the sensitivity and accuracy. Thus using the graph below, I was able to calculate the minimum weight measurable by dividng the maximum load by the number of divisions to get about 0.03g. </br> &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/load_cell_resolution.png" width="500" height="300">  </br> The QR scanner module supported UART serial communcation. Thus I had to make a connection between the RX (receive) and TX (transmit) pins between the host (microcontroller) and the device (QR scanner). After some trial and error, I was actually able to get some raw readings of the QR scans.


## Week of 2022-04-11
* **04/11 (Software QR Complete)**:
  * <ins>Objectives</ins>: Complete software code and testing for QR scanner
  * <ins>Overview</ins>: Even though I was able to get the QR code readings using the module, there were several issues that I had to fix. One was that the reading values kept changing even for the same QR code. I realized that there were two different types of QR codes, dynamic and statc. Dynamic QR codes had their encoded information change upon creation as it was a redirection to a URL whereas static QR codes had their information fixed. Since our project only required QR codes for validation of the G2G containers, I used static QR codes to read the data. Another issue was that if the returned container sat in the return place for too long, it would get multiple QR scans and fill up the serial communication buffer. Thus next time the machine was used, it gets tricked into thinking that it already has a valid QR scan. To solve this issue, I had to clear the buffer if and only if the container was invalid. I also had to send several UART scan commands to the address of the QR to change some of the default behaviors that were incompatible with the intended design of our project. First change was to set the baud rate from 9600 to 115200 to be synchronized with the card reader, and next was changing the scan mode from sleep to continuous scanning mode. Last step was setting a manual timeout value of 10 seconds to allow users ample time to place and return an old container. After all these configurations, the below code shows what I had used to read in QR data.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/QR_code.png" width="500" height="400"> 

* **04/12 (Software Card Reader Code)**:
  * <ins>Objectives</ins>: Software code for usb magnetic card swiper
  * <ins>Overview</ins>: I started working on the card swiper but spent numerous hours just debugging to get it to work. This was because the card reader was a HID device and had complex USB protocols that I had to go through. The initial model we were using was a MSR123 card reader. As it failed to initialize, I started looking into the product ID as well as the vendor ID and saw a mismatch between what my computer had detected and what my software code had detected. It was failing to retrieve the device descriptor for the specific USB device. I tried making tweaks in the code to store larger bits for the ID as there was a huge mismatch, but no sort of available driver code was able to get the card initialized.

* **04/13 (Card Reader Code Failure & Debugging)**:
  * <ins>Objectives</ins>: Final debugging of the card reader
  * <ins>Overview</ins>: After multiple attempts, I went line by line within the Arduino library to find the point of failure, and identified it to be in the below code. When I declared a USB object within the software, it went through a list of initialization processes to find the device descriptor and storing the end-point address of the device. However it was unable to do so, and I realized that I either had to write a separate driver code (which was impossible with the time constraint I had) or find another HID device compatible with existent driver codes.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/usb_err.png" width="550" height="300"> 

* **04/14 (Card Reader Alternative Solution)**:
  * <ins>Objectives</ins>: Design consideration for the card reader
  * <ins>Overview</ins>: After multiple failures with the card reader, I started thinking about different alternatives. Many teams have been using a RFID tags for ID verification and I also thought about moving to this method. However not only did this incur additional cost as well as delaying the progress with delivery time, it didn't accomodate the intended design of our machine as we wanted it to be available exlcusively to the U of I students using their iCards. Using RFID cards meant that the project was just a proof of concept that has very little practical use as it meant all students would have to purchase a RFID tag. Thus I decided to stick with a card swiper but looked for different models.

* **04/15 (Card Reader MSR90)**:
  * <ins>Objectives</ins>: Card reader code using MSR90
  * <ins>Overview</ins>: The unsuccessful attempts with MSR123 led me to try with another model called MSR90. Forunately after some tweaking, I was able to get the card reader to initialize. One major modification I had to do was so that it would read all different kinds of magnetic stripe cards, but only parse the data for iCards (and not credit cards, etc). This was done by modifying the interrupt response of the device. Card readers act similar to USB HID Keyboard device descriptor as it responds to both key up and key down interrupts. The image below shows the different interrupts that a card swipe and keyboard responds to. The card reader also responded to presses of special key characters like SHIFT and CAPS, which wasn't what I wanted for the project. Magnetic cards usually have three tracks and each track is separated by some special character, which was why the interrupt was happening for RIGHT SHIFT and so on. After getting rid of some of the interrupts, I was able to read in actual data from each card swipe.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/HIDkb.png" width="600" height="300"> 

* **04/16 (Software Card Reader Complete)**:
  * <ins>Objectives</ins>: Finish up the software code for magnetic card reader
  * <ins>Overview</ins>: The last step of the card reader required data parsing. Because the card swipe was sending three different tracks of information, I had to identify which track was relevant and which data to parse. After the final parsing I was able to identify each iCard swipe to be of a CARDHOLDER/UNIVERSITY card as well as reading in the UIN (unifersity identification number).

* **04/17 (Software Code Integration)**:
  * <ins>Objectives</ins>: Integrate all software codes
  * <ins>Overview</ins>: After individual testing of each module, I had to put these back into the original FSM code that I had written to get the entire functionality of the machine working. Since we were using on-chip memory to store user information such as the number of available tokens, I created a student struct for each user as below. Each student is identified by his or her UIN along with the name, and the data stores the number of tokens as well. The final integration and output of our machine is posted on YouTube, and the link is shown under 04/24 (Final Wrap Up and Enclosure) in section [Week of 2022-04-18](#week-of-2022-04-18).

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/student_struct.png" width="250" height="150"> 

## Week of 2022-04-18
* **04/19 (LCD Display and LED)**:
  * <ins>Objectives</ins>: Design decision between LCD and LEDs and finish software code for status messages
  * <ins>Overview</ins>: Initially I thought of having a LCD display screen for UI subsystem, but realized that the machine was intended to behave in a similar manner to that of a normal vending machine, which meant that there was little to no information to convey to users. Most information was abstracted away for security reasons and thus the final design decision I made was using LED status messages. This was done using LEDs for 6 different states and using a multiplexer to cut down on the number of wires. The table below shows the 8-to-1 demux outputs based on the three select pins A0, A1, A2. </br> <img src="/images/demux.png" width="600" height="300">  </br> The LEDs were then controlled within the code using a helper function shown below.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <img src="/images/mux_code.png" width="350" height="150"> 

* **04/22 (Mock Demo)**:
  * <ins>Objectives</ins>: Mock demonstration with our TA
  * <ins>Overview</ins>: We did our mock demosntration just in front of our TA and received feedback on certain parts. We were told to have an enclosure for our machine so that all components are well hidden from an outside user. The functionality was mostly achieved, but there were some minor things that I still had to work on.

* **04/23 (Final Debugging and LED Status Message)**:
  * <ins>Objectives</ins>: Finalize and complete on the functionality part of the project
  * <ins>Overview</ins>: Most of the software and hardware components were complete at this point, and I had to ensure that everything was working as expected for the final demo. I ran through several different testcases for our machine and also wrote the status messages on top of the LEDs.

* **04/24 (Final Wrap Up and Enclosure)**:
  * <ins>Objectives</ins>: Finalize and complete the entire project
  * <ins>Overview</ins>: Incorporating the feedback we received from the mock demo, we completed the enclosure for our machine so that all things were abstracted away. We also made certain openings for the enclosure so that any "authorized" individuals were allowed to collect returned containers and refill new containers. The below link shows the functionality of our entire project and the two gifs below demonstrate how the sensor and control subsystem work together to complete the retrieval and dispensing system.
  * <ins>YouTube link</ins>: https://www.youtube.com/watch?v=p8fdRb78moU

<p align = "center">
<img src = "https://cdn.discordapp.com/attachments/903401697957789716/971312833566486598/retrieve.gif">
<img src = "https://cdn.discordapp.com/attachments/903401697957789716/971312807532458034/dispense.gif">
</p>

<p align = "center">
 <strong>Retrieval (Left) and Dispensing (Right)</strong>
</p>

## Week of 2022-04-25
* **04/26 (Final Demo)**:
  * <ins>Objectives</ins>: Complete final demonstration
  * <ins>Overview</ins>: We did our final demonstration in front of our TA, professor Song as well as some other individuals who wanted to attend our presentation.

* **04/27 (Presentation Slides)**:
  * <ins>Objectives</ins>: Work on presentation slides and final report
  * <ins>Overview</ins>: After the final demo was over, there were only two major components left, which were the final presentation and the final report. I took this week to complete some of the design and software components for both the presentation and the report. I also arranged our team meetings to get together and rehearse.

## Week of 2022-05-02
* **05/03 (Final Presentation)**:
  * <ins>Objectives</ins>: Deliver our final presentation
  * <ins>Overview</ins>: Similar to the final demo, we had our final presentation in front of our TA, professor Song, and some individuals who wanted to attend. This took about 20 minutes along with 5 extra minutes for additional Q&A.

## References
* Adafruit, Continuous Rotation Servo - FeeTech FS5103R. [Online]. Available: https://media.digikey.com/pdf/data%20sheets/adafruit%20pdfs/154_web.pdf. [Accessed: 02-May-2022].
* “QR code vs Barcode: Why the difference matters,” Paysley Blog, 10-Feb-2022. [Online]. Available: https://paysley.com/blog/qr-code-vs-barcode/. [Accessed: 03-May-2022].
* “Resistors for led circuits: Resistor applications: Resistor Guide,” EEPower. [Online]. Available: https://eepower.com/resistor-guide/resistor-applications/resistor-for-led/#. [Accessed: 03-May-2022].
* “RFID scanner - full tutorial,” Arduino Project Hub. [Online]. Available: https://create.arduino.cc/projecthub/shubamtayal/rfid-scanner-full-tutorial-6518db. [Accessed: 03-May-2022].
* “Stepper vs Servo,” Tutorial: Stepper vs Servo. [Online]. Available: https://www.amci.com/industrial-automation-resources/plc-automation-tutorials/stepper-vs-servo/. [Accessed: 03-May-2022].
* “Tal221 miniature load cell - cdn.sparkfun.com.” [Online]. Available: https://cdn.sparkfun.com/assets/9/9/a/f/3/TAL221.pdf. [Accessed: 02-May-2022].
* University Housing, “Good2Go carry-out program,” University Housing. [Online]. Available: https://housing.illinois.edu/Dining/Locations/Good2Go-Carry-Out-Program. [Accessed: 30-Apr-2022].



