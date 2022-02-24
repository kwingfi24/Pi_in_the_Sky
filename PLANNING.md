# Planning
Engineering 4 - Project Proposal

## Table of Contents
* [Scope and Function](#Scope_and_Function)
* [Bill of Materials](#Bill_of_Materials)
* [Diagrams](#Diagrams)
* [Schedule](#Schedule)
* [Block Code Diagram](#Block_Code_Diagram)
* [Risk Mitigation](#Risk_Mitigation)
---

## Scope_and_Function
#### How will the final product function?

In this project we will be making a plane with hang glider like wings. Within the plane glider, there will be a pi along with some other things to take some data of the flight as well as pictures. The OLED Display and accelerometer will be used to graph the movement of the plane glider while a pi camera will be taking pictures of the ground from the bottom of the glider. 

#### What materials will be needed and how much?

For the wings, we will be using cardboard. Most of the body of the plane will be in wood, but with a 3D printed nose in order for it to be in a more rounded shape. We are making the plane glider as small as possible to keep it light and easy to launch, so we will not be using a lot of materials. The most material will be the wood due to the octogonish shape of the plane glider. However, due to the size, we should be able to get by with only a sheet or two of wood with the same thickness as the acrylic. Wood is being used rather than acrylic so that it can withstand a bit more of an impact. 

#### What do you still need to learn for the project?

We need to learn a bit more about how the accelerometer and OLED display work. Graphing the flight without filling the screen could be a problem. To accommodate for this, we might need a bigger OLED screen, but I’m not seeing any in the lab. Instead we might need to graph fewer points rather than all of them to not fill the screen. We also will need to learn how to have things falling from the plane glider without interfering with the flight. This should be combated with them being released facing the opposite direction of the plane glider’s flight. If this does not work, changes will need to be made with either a change of what is dropping, how much is dropping, and the falling speed/time of the objects falling. 

#### What is the definition for "success" in the project?

The definition of success for this project will be growing and learning about things we didn’t previously know, having a working project by the middle of May, and getting some awesome pictures from the flight.


## Bill_of_Materials (for now)
- LSM303
- OLED Display
- Pi Camera
- 2 Buttons
- 2 LEDS
- 2 Servos
- Switch
- Rubberband

Materials
- Cardboard for wings
- Wood for plane body
- 3D printed nose

## Diagrams
Paper:

![image](https://user-images.githubusercontent.com/60272021/153009169-bfc58da1-c097-4e1e-9e28-fedd38d4bfe2.png)

CAD:

<img src="https://github.com/kwingfi24/Pi_in_the_Sky/blob/main/Screenshot%202022-02-10%209.57.14%20AM.png?raw=true">

image

Onshape link: https://cvilleschools.onshape.com/documents/0d1477f4cea9ecd25f6723da/w/6727ffede59d5bf3646c2d1f/e/270201424a55e257cf29338d

## Schedule
We have planned for this project to last for 15 and a half weeks. Starting on Feb 1 (Including planning time) and ending on May 19. Presentation day is _.
- [x] Initial Design (paper) including rough measurements - Tues, Feb 8
- [x] Accelerometer and OLED Display - Tues, Feb 15
- [x] Initial Design (CAD) including any measurements - Thurs, Feb 17
- [ ] Pi Camera with button - Mon, Feb 28
- [ ] Testing flying capability of original design - Mon, Feb 28
- [ ] Putting pieces of the code together - Tues, Mar 1  
- [ ] Working with no screen - Thurs, Mar 3
- [ ] Battery powered - Thurs, Mar 3
- [ ] Build prototype #1 (possibly testing without all pieces)- Thurs, Mar 3
- [ ] Testing that prototype - Tues, Mar 8
- [ ] Tweaking design and/or code - Mon, Mar 14
- [ ] Build prototype #2 / Update prototype #1 - Tues, Mar 15
- [ ] Testing that prototype - Thurs, Mar 17
- [ ] Tweaking design and/or code - Mon, Mar 21
- [ ] Finalize CAD Design - Mon, Mar 28
- [ ] Wiring condensed - Tues, Mar 22
- [ ] Diagram and commented code - Tues, Mar 22
- [ ] Soldering - Mon, Mar 28
- [ ] Build launcher prototype - Thurs, Mar 31
- [ ] Testing launcher - Mon, Apr 4
- [ ] Tweaking and retesting - Thurs, Apr 7 (Work on this until stuff is done printing/cutting)
- [ ] Printing/Cutting - Thurs, Apr 7 (May change do to fast or slow printing/cutting)
- [ ] Assembly - Tues, Apr 12
- [ ] Testing and small tweaks - Thurs, May 12
- [ ] Documantation and Github organizing/update or any final presentation parts - Thurs, May 19
- [ ] Presenting finished product - 

## Block_Code_Diagram
#### Accelerometer and OLED Display
Ran similarly as the Headless Accelerometer assignment, but instead of displaying the reading, it shows the parabola of the launch. Using the reading, it will “graph” the parabola by putting dots on the screen and moving a little right each time without clearing the screen. Under the graph it will be showing the highest height it’s reached so far, meaning it will stop at when it reached its climax. To do this, the bottom area will have to be cleared without erasing the graph. *If there is a way to store the acceleration readings and send them to github or something, we should try it. ***If the project  accidentally turns upside down, will this mess up the reading?
#### Pi Camera
Similarly to the Copypasta assignment, the camera will take pictures consecutively every so often (time not determined yet). It will need to take pictures without having a button pressed which is different from the Copypasta assignment. After taking the pictures, it should push them to github individually as well as come together as a gif/stop motion video. It’s also a possibility to take a video alone rather than a bunch of individual pictures. The camera should only start recording or taking pictures when the project is being thrown to when it hits the ground. This could be done with a button that starts the camera when pushed and  then stops the camera when that same button is pushed again.
#### LEDs
These will be used as indicators. The first LED will show that the power is on. The second one will start the running of the camera and accelerometer/graphing on the OLED. The final one will indicate that the shutdown button has been pressed (this one might not be used). 
#### Servo
This will act as a way to open the door(s) on the bottom of the pi at the apex. This will be pretty easy to set up. We do need to take weight into consideration along with the possibility of the objects falling out interfering with the fall of the actual pi. The door will need to be open long enough to drop, but be closed by the time it hits the ground. This could be difficult depending on how fast the project will fall. Since the plane/glider shape and appearance I believe it would be funny if we had soldiers or people falling out with parachutes.
#### Shutdown Button
This button will shutdown the pi before turning it off. A button will be needed because of the lack of a screen and keyboard.
#### On/Off Switch
Obviously turns the project off and will need to connect and unconnect the battery to the rest of the device.

## Risk_Mitigation
The only real risks I see is possibly with the soldering or launching/testing of the launching. As of right now, the plane glider will be sent up by a make shift slingshot. We can be careful and cautious in many ways such as having other stand away from lanchings, aiming at an open space, and making sure no pieces are going to fly off. If there are going to be two people launching, the person in front (holding the stick) will be out of the way enough so that the can hold it, but not be in the plane gliders path. With having things fall when the project hits the apexs, could also have a bit of a risk becuase of what and how fast the object is falling. To combat this, the things falling should be smaller and lighter objects, possibly ribbons or something of that sort.

