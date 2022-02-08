Team Members:

Ariocie Liang (arliang2), John Kim (jaehank2), Henry Guan (henryg3)

## PROBLEM

Good2Go (G2G) containers are used all throughout dining halls for individuals wanting to take their food to go. The program allows you to trade in an old container for a token, where that token can then be used to trade for a new container. This is a hassle for both parties that handle the entire process. It's very redundant and can be streamlined/improved with mechanical assistance.

## SOLUTION

Our solution involves a token/food container swapping machine that serves 2 main functions:

Have a G2G token, that upon deposit, returns a clean container
Accept a used container, returning a G2G token or a clean container
The goal here is to make the process semi-autonomous by removing 2 stages of interaction, as well as speeding up the entire process by doing so.

# SUBSYSTEMS

## Initial State:
The initial state of the machine will be waiting for user input for either an {old container} or a {token}, which is read by the microcontroller

## Display Screen and Buttons:

The display screen along with the button is used to guide the user into selecting one of the two options. The first selection is {old container} and {token} which is used to inform the machine what it’s supposed to expect from the user. In the case of the {token}, the machine will read from the card swipe. The next option that will be displayed is {new container} and {token} which occurs in the event the user returns an old container. Based on the input, the machine will return either a new container or update the token info from the swiped card.

## Sensors:

QR scanner to identify valid containers by reading the food container ID and a wifi module to send it over to the microcontroller. If it is an invalid ID, the machine returns to its initial state. Otherwise, the machine will dispense either a {new container} or generate a {token}
Scale to measure weight so that once it exceeds {container weight + constant}, the machine will not accept the container and will return to its initial state. If the weight is within the threshold, the machine will dispense either a {new container} or generate a {token}
Card Swipe is used to process digital coins instead of physical ones. Each card will hold information of the number of tokens and will get updated for every swipe. If a card swipe is read from the initial state, the machine will dispense a new container


## Microcontrollers:

Microcontroller will keep track of the state transitions and will also be responsible for activating different motors and reading data from the scale, token as well as the food container ID. From the initial state (old container, token), if the user inputs an old container, the microcontroller will take input from the scale and activate the motor to receive the returned old container, and then wait for further user input for {new container} or a {token}. Otherwise if the user selects a token, the microcontroller will process the token and activate the motors to dispense a new container.

## Motors:

Motors will be wired to a pair of arms near the opening of where the user can place an old container. It will be placed on the same surface as the scale (on the bottom of the old container) so that once the motors are activated, it lifts up and acts as the pushing mechanism to deposit the old containers.
A different set of motors wired to two arms (spaced for a single container) will also be used to dispense new containers. Only a single container will be preloaded in between the arms, with the rest being loaded behind this single container at an angle. Upon the activation of the motors, the first arm closest to the drop chute will open first, dispensing the container. That arm will then close, followed by the second arm opening, allowing one container through. That barrier will then close, completing the process of preloading another container that's ready to dispense. 


CRITERION FOR SUCCESS

User should be able to start the process by pressing a button, selecting whether they are depositing a valid token or a used G2G container.
When a valid token is deposited, the machine should dispense a clean container and reset. If token is invalid, return token and reset.
When a G2G container is deposited, the machine should check that the container is valid (has a valid bar code and is not over a set weight limit)
If the deposited container is overweight, the machine waits for the user to pick up the container, clear it out, and set it down again.
Else, it will ask the user to select either a token or a clean container to be dispensed.
the machine will then dispense selected object and reset.
In total the entire process should take a minute per person to complete!

