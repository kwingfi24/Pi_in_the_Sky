# Planning
Engineering 4 - Project Proposal

## Table of Contents
* [Bill of Materials](#Bill_of_Materials)
* [Diagrams](#Diagrams)
* [Schedule](#Schedule)
* [Block Code Diagram](#Block_Code_Diagram)
* [Risk Mitigation](#Risk_Mitigation)
---

## Bill_of_Materials (for now)
- LSM303
- OLED Display
- Pi Camera
- 2 Buttons
- 3-4 LEDS
- Servo?
- Switch

## Diagrams


## Schedule
- [x] Initial Design (paper) including any measurements - Tues, Feb 8
- [ ] Accelerometer and OLED Display - Mon, Feb 14
- [ ] Pi Camera with button - Thurs, Feb 17
- [ ] Lights and opening door - Thurs, Feb 17
- [ ] Initial Design (CAD) including any measurements - Thurs, Feb 17
- [ ] Working with no screen - Tues, Feb 22
- [ ] Battery powered - 
- [ ] Build prototype #1 - 
- [ ] Testing that prototype - 
- [ ] Tweaking design and/or code - 
- [ ] Build prototype #2 - 
- [ ] Testing that prototype - 
- [ ] Tweaking design and/or code - 
- [ ] Finalize CAD Design - 
- [ ] Printing/Cutting - 
- [ ] Wiring condensed - 
- [ ] Diagram and commented code - 
- [ ] Soldering - 
- [ ] Assembly - 
- [ ] Testing - 
- [ ] Small tweaks (if any) - 
- [ ] Presenting finished product - 

## Block_Code_Diagram
#### Accelerometer and OLED Display
Ran similarly as the Headless Accelerometer assignment, but instead of displaying the reading, it shows the parabola of the launch. Using the reading, it will “graph” the parabola by putting dots on the screen and moving a little right each time without clearing the screen. Under the graph it will be showing the highest height it’s reached so far, meaning it will stop at when it reached its climax. To do this, the bottom area will have to be cleared without erasing the graph. *If there is a way to store the acceleration readings and send them to github or something, we should try it. ***If the project  accidentally turns upside down, will this mess up the reading?
#### Pi Camera
Similarly to the Copypasta assignment, the camera will take pictures consecutively every so often (time not determined yet). It will need to take pictures without having a button pressed which is different from the Copypasta assignment. After taking the pictures, it should push them to github individually as well as come together as a gif/stop motion video. It’s also a possibility to take a video alone rather than a bunch of individual pictures. The camera should only start recording or taking pictures when the project is being thrown to when it hits the ground. This could be done with a button that starts the camera when pushed and  then stops the camera when that same button is pushed again.
#### LEDs
This is one thing that will happen when the pi believes it has reached its apex. Three LEDs with different colors blinking in a pattern. *Possibly add a fourth LED to show that the power is on.
#### Servo
This will act as a way to open the door(s) on the bottom of the pi and the apex too. This will be pretty easy to set up. We do need to take weight into consideration along with the possibility of the objects falling out interfering with the fall of the actual pi. The door will need to be open long enough to drop, but be closed by the time it hits the ground. This could be difficult depending on how fast the project will fall.
#### Shutdown Button
This button will shutdown the pi before turning it off. A button will be needed because of the lack of a screen and keyboard.
####On/Off Switch
Obviously turns the 

## Risk_Mitigation


