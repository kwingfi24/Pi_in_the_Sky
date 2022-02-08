# Pi_in_the_Sky
Engineering 4 - Project

## Table of Contents
* [Planning](#Planning)
---

## Planning
### Scope and Function
In this project we will be making a plane with wings that are like a hang glider. Within this boy, there will be a pi along with some other things to take some data of the flight as well as pictures. The OLED Display and accelerometer will be used to graph the movement of the plane glider while a pi camera will be taking pictures of the ground from the bottom of the glider. For the wings, we will be using cardboard. Most of the body of the plane will be in wood, but with the nose 3D printed to be in a more rounded shape. We are making the plane glider as small as possible to keep it light and easy to launch, so we will not be using a lot of cardboard or the 3D printer. The most material will be the wood due to the octogonish shape of the plane glider. Wood is being used rather than acrylic so that it can withstand a bit more of an impact. However, due to the size, we should be able to get by with only using 1 or 2 sheets of acrylic. We need to learn a bit more about how the accelerometer and OLED display work. Graphing the flight without filling the screen could be a problem. To accommodate for this, we might need a bigger OLED screen, but I’m not seeing any in the lab. Instead we might need to graph fewer points rather than all of them to not fill the screen. We also will need to learn how to have things falling from the plane glider without interfering with the flight. This should be combated with them being released facing the opposite direction of the plane glider’s flight. If this does not work, changes will need to be made with either a change of what is dropping, how much is dropping, and the falling speed/time of the objects falling. The definition of success for this project will be growing and learning about things we didn’t previously know, having a working project by the middle of May, and getting some awesome pictures from the flight.

### Bill of Materials
- LSM303
- OLED Display
- Pi Camera
- 2 Buttons
- 2 LEDS
- 2 Servos
- Switch
- Rubberband


- Cardboard material or wings
- Wood for plane body
- 3D printed nose

### Diagrams
![image](https://user-images.githubusercontent.com/60272021/153009169-bfc58da1-c097-4e1e-9e28-fedd38d4bfe2.png)

### Milestones
- [x] Brainstorm ideas
- [ ] Develop an initial design (pencil and paper, CAD, etc.)
- [ ] Construct a prototype
- [ ] Test your design
- [ ] Refine/optimize your design
- [ ] Present finished product

### Block Code Diagram
#### Accelerometer and OLED Display
Ran similarly as the Headless Accelerometer assignment, but instead of displaying the reading, it shows the parabola of the launch. Using the reading, it will “graph” the parabola by putting dots on the screen and moving a little right each time without clearing the screen. Under the graph it will be showing the highest height it’s reached so far, meaning it will stop at when it reached its climax. To do this, the bottom area will have to be cleared without erasing the graph. *If there is a way to store the acceleration readings and send them to github or something, we should try it. ***If the project  accidentally turns upside down, will this mess up the reading?
#### Pi Camera
Similarly to the Copypasta assignment, the camera will take pictures consecutively every so often (time not determined yet). It will need to take pictures without having a button pressed which is different from the Copypasta assignment. After taking the pictures, it should push them to github individually as well as come together as a gif/stop motion video. It’s also a possibility to take a video alone rather than a bunch of individual pictures. The camera should only start recording or taking pictures when the project is being thrown to when it hits the ground. This could be done with a button that starts the camera when pushed and  then stops the camera when that same button is pushed again.
These will be used as indicators. The first LED will show that the power is on. The second one will start the running of the camera and accelerometer/graphing on the OLED. The final one will indicate that the shutdown button has been pressed (this one might not be used). 
#### Servo
This will act as a way to open the door(s) on the bottom of the pi at the apex. This will be pretty easy to set up. We do need to take weight into consideration along with the possibility of the objects falling out interfering with the fall of the actual pi. The door will need to be open long enough to drop, but be closed by the time it hits the ground. This could be difficult depending on how fast the project will fall.
#### Shutdown Button
This button will shutdown the pi before turning it off. A button will be needed because of the lack of a screen and keyboard.
#### On/Off Switch
Obviously turns the project off and will need to connect and unconnect the battery to the rest of the device.


