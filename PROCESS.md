# Pi_in_the_Sky
Engineering 4 - Project

## Table of Contents
* [Planning](#Planning)
* [One_Month_Check_In](#One_Month_Check_In)
* [Start_Of_May_Check_In](#Start_Of_May_Check_In)
* [Test_1](#Test_1)
---

## Planning
### Scope and Function
#### How will the final product function?

In this project we will be making a plane with hang glider like wings. Within the plane glider, there will be a pi along with some other things to take some data of the flight as well as pictures. The OLED Display and accelerometer will be used to graph the movement of the plane glider while a pi camera will be taking pictures of the ground from the bottom of the glider. 

#### What materials will be needed and how much?

For the wings, we will be using cardboard. Most of the body of the plane will be in wood, but with a 3D printed nose in order for it to be in a more rounded shape. We are making the plane glider as small as possible to keep it light and easy to launch, so we will not be using a lot of materials. The most material will be the wood due to the octogonish shape of the plane glider. However, due to the size, we should be able to get by with only a sheet or two of wood with the same thickness as the acrylic. Wood is being used rather than acrylic so that it can withstand a bit more of an impact. 

#### What do you still need to learn for the project?

We need to learn a bit more about how the accelerometer and OLED display work. Graphing the flight without filling the screen could be a problem. To accommodate for this, we might need a bigger OLED screen, but I’m not seeing any in the lab. Instead we might need to graph fewer points rather than all of them to not fill the screen. We also will need to learn how to have things falling from the plane glider without interfering with the flight. This should be combated with them being released facing the opposite direction of the plane glider’s flight. If this does not work, changes will need to be made with either a change of what is dropping, how much is dropping, and the falling speed/time of the objects falling. 

#### What is the definition for "success" in the project?

The definition of success for this project will be growing and learning about things we didn’t previously know, having a working project by the middle of May, and getting some awesome pictures from the flight.

### Bill of Materials
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

### Diagrams
Paper:

![image](https://user-images.githubusercontent.com/60272021/153009169-bfc58da1-c097-4e1e-9e28-fedd38d4bfe2.png)

CAD:

<img src="https://github.com/kwingfi24/Pi_in_the_Sky/blob/main/Screenshot%202022-02-10%209.57.14%20AM.png?raw=true">

image

Onshape link: https://cvilleschools.onshape.com/documents/492561168bf6b91a97d77a47/w/45d7efb3da141b22b711ac96/e/4b3a4ccdc809ca3a080ae7f4

### Schedule
We have planned for this project to last for 15 and a half weeks. Starting on Feb 1 (Including planning time) and ending on May 19. Presentation day is _.
- [x] Initial Design (paper) including rough measurements - Tues, Feb 8
- [x] Accelerometer and OLED Display - Tues, Feb 15
- [x] Initial Design (CAD) including any measurements - Thurs, Feb 17
- [x] Pi Camera with button - Mon, Feb 28
- [x] Lights for apex - Mon, Feb 28
- [X] Testing flying capability of original design - Mon, Feb 28
- [X] Putting pieces of the code together - Tues, Mar 1  
- [ ] Working with no screen - Thurs, Mar 10
- [ ] Battery powered - Thurs, Mar 10
- [x] Build prototype #1 (possibly testing without all pieces)- Thurs, Mar 13
- [x] Testing that prototype - Tues, Mar 14
- [x] Tweaking design and/or code - Mon, Mar 15
- [ ] Build prototype #2 / Update prototype #1 - Tues, Mar 16
- [ ] Testing that prototype - Thurs, Mar 17
- [ ] Tweaking design and/or code - Mon, Mar 21
- [ ] Finalize CAD Design - Mon, Mar 28
- [x] Wiring condensed - Tues, Mar 22
- [x] Diagram and commented code - Tues, Mar 22
- [ ] Soldering - Mon, Mar 28
- [x] Build launcher prototype - Thurs, Mar 31
- [x] Testing launcher - Mon, Apr 4
- [ ] Tweaking and retesting - Thurs, Apr 7 (Work on this until stuff is done printing/cutting)
- [x] Printing/Cutting - Thurs, Apr 7 (May change do to fast or slow printing/cutting)
- [x] Assembly - Tues, Apr 12
- [ ] Testing and small tweaks - Thurs, May 12
- [ ] Documantation and Github organizing/update or any final presentation parts - Thurs, May 19
- [ ] Presenting finished product - 

### Block_Code_Diagram
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

### Risk_Mitigation
The only real risks I see is possibly with the soldering or launching/testing of the launching. As of right now, the plane glider will be sent up by a make shift slingshot. We can be careful and cautious in many ways such as having other stand away from lanchings, aiming at an open space, and making sure no pieces are going to fly off. If there are going to be two people launching, the person in front (holding the stick) will be out of the way enough so that the can hold it, but not be in the plane gliders path. With having things fall when the project hits the apexs, could also have a bit of a risk becuase of what and how fast the object is falling. To combat this, the things falling should be smaller and lighter objects, possibly ribbons or something of that sort.

### Milestones
- [x] Brainstorm ideas
- [X] Develop an initial design (pencil and paper, CAD, etc.)
- [X] Construct a prototype
- [X] Test your design
- [ ] Refine/optimize your design
- [ ] Present finished product

## One_Month_Check_In
#### This update is from March 1 (a month after the project has started)
### What have we done?
In this month we have made a design for the plane and have printed mutiple to test the flight capability of it. There has been a total of 3 versions of the plane that change size, center of gravity points, and angles of wings. We have also finished most of the code other than a few things. The lights have been figured out, the accelerometer/OLED screen is done, and most of the iring is pretty final. So far we have been able to stay mostly on schedule, but we have run into a few bumps where we had to spend an extra bit of time on some things. We have found multiple helpful websites that have helped along the way.

### What still need to be done?

A few tasks still need to be done befre we can move onto the testing and refining stages of the project. On the coding/wiring side of things, the code working together and without being attached to a computer still needs to be figured out. Making it battery operated and soldering pieces together also needs to be completed within the next few weeks.

### Where are we struggling?

The planes keep flipping going front first. There was too much weight in the front, so we changed the design. We are trying to distribute the weight evenly, but without the pi and everything inside, it is a bit difficult to gage. We are waiting to change it anymore until we are able to test everything together for the first time. The pi camera gave us a lot of trouble. I tried many different ways and still have not settled on a particular one. 

### What has been changed?
The plane is no longer closed, rather it is two sides with an open middle. It is also going to be made only out of cardboard to improve durability and weight. The wings have also changed a lot. There are now two sets of wings. In the final design (for now) both set of wings are curved and angled. We are no longer going to be dropping things from the plane. There will only be lights as of right now. We got rid of the things falling to get rid of some of the weight and in the interest of time. We could possibly add this or another thing back to the project if time allows. 

### Bill of Materials
- LSM303
- OLED Display
- Pi Camera
- 2 Buttons
- 6 LEDS
- Switch
- Rubberband

Materials
- Cardboard

### Pictures/Diagrams
#### Design

Link to Onshape Document: https://cvilleschools.onshape.com/documents/492561168bf6b91a97d77a47/w/45d7efb3da141b22b711ac96/e/4b3a4ccdc809ca3a080ae7f4
### In Onshape

### Version 3 (Final as of right now)

![Screenshot 2022-03-03 9 52 52 AM](https://user-images.githubusercontent.com/60272021/156589460-5ff91dea-edbb-4563-aca9-adfe65bd77a1.png)

### Laser Cut

#### Version 1

![Screenshot 2022-03-03 9 59 49 AM](https://user-images.githubusercontent.com/60272021/156590828-7085db7d-46a6-4710-9ebc-519f81f610b8.png)

#### Version 2 - Added a second set of wings

![Screenshot 2022-03-03 10 00 05 AM](https://user-images.githubusercontent.com/60272021/156590900-1bf0d4be-968a-4302-82c7-9ed34e270bba.png)

Final Printed - Angled and curved wings

![Screenshot 2022-03-03 10 24 57 AM](https://user-images.githubusercontent.com/60272021/156595463-9ebacbb5-0c09-4814-a178-cf23a2143108.png)

#### Wiring
Wiring - Better pictures/diagrams will come

![Screenshot 2022-03-03 9 36 39 AM](https://user-images.githubusercontent.com/60272021/156586159-3fd2d8d5-d540-4465-90f7-1111caf976b9.png)

#### Code snipets

Accelerometer/OLED Screen
```
while True:    
    accel, mag = lsm303.read()
    # Grab the X, Y, Z components from the reading and print them out.
    accel_x, accel_y, accel_z = accel
    mag_x, mag_y, mag_z = mag

    # change in x and z values
    a = direction(x)
    b = direction(height)
    
    # "Graphing" the x values by drawing circles/plotting point every second
#    draw.ellipse((x+50+a, top+25, x+shape_width+50+a, bottom-25), outline=225, fill=225) # x values
#    draw.ellipse((x+50, top+b, x+shape_width+50, top+shape_height+b), outline=225, fill=225) # z values
    draw.ellipse((x+a, top+b, x+shape_width+a, top+shape_height+b), outline=225, fill=225) # both values
    
    
    # Write readings for x and y
    draw.text((x, bottom-10), f'X: {(round (quotient(accel_x, scale), 2))}',  font=font, fill=255)
    draw.text((x+60, bottom-10), f'Z: {(round (quotient(accel_z, scale1), 2))}', font=font, fill=255)
    # Wait half a second and repeat.
    time.sleep(.5)
    # Display image.
    disp.image(image)
    disp.display()
    # clear just the bottom leaving the points there to look at
    draw.rectangle((0,bottom-20,width,bottom), outline=0, fill=0)
```
Pi Camera
```
with picamera.PiCamera() as camera: # this will take 13 photos within 6 seconds
  camera.start_preview()
  time.sleep(2) # this will give us 2 seconds to get the plane in the air before it starts taking pictures
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5) # this will give us half a second before the next picture
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5)
  camera.capture('img{counter:02d}.jpg')
  time.sleep(.5) # half a second before the program stops
  camera.capture('img{counter:02d}.jpg') #last picture
```
LEDS
```
leds.on()
sleep(1)
leds.off()
sleep(1)
leds.value = (1, 0, 0, 0, 0, 1)
sleep(1)
leds.value = (0, 0, 1, 1, 0, 0)
sleep(1)
leds.value = (0, 1, 0, 0, 1, 0)
sleep(1)
leds.blink()
```

## Start_Of_May_Check_In
#### This update is from May 3 (a little less than a month before the project is done)

#### This is after the one month break for Onshape

### What still need to be done?

#### Design/Cut

Until testing, there isn't a ton we can do here, but we possibly will need to change things depending on how it works while testing. It is very possible that a design change will be necessary. We also need to figure out placement and attachment of the pieces. 

#### Coding/Wiring

Sadly, the few tasks from the one month still need to be done before we can move onto the testing and refining stages of the project. We had trouble with the pi and it hung us up, but the code is complete. On the coding/wiring side of things, the code working together and without being attached to a computer still needs to be figured out. Making it battery operated and soldering pieces together also needs to be completed within the next few weeks.

#### Overall

Overall we still need to test with the weight on the plane and tweak from there. After all of the tweaking, we will need to finalize the design as well as the code, eventually ending with the presentation of the final. There is also a week where we are going to lose time due to 2 hour delays, and another week where one teammate will not be here. To get around this, we will have to work fast, but careful to not make too many mistakes as well as possibly spending extra time in the lab before, after, and during the school day.

## Test_1
### How did it go?

### What worked and what didn't?
In this first flight, we did not test the lights (thing that happens at the apex of flight). This was simply due to a lack of time and problems with the pi. With information on how all other aspects worked, we will be able to move on from there. 
##### Code: 
Comments are in the code
```
try:
    print('Press the left (yellow) button to start. Press the right (grey) button to stop.')
    while True:
        input_state = GPIO.input(leftbutton) # reading the button state until pressed
        if input_state == False:
            print('left button was pressed!')
            sleep(2)  
            while True: 
               input_state1 = GPIO.input(rightbutton)
               accel, mag = lsm303.read()
               # Grab the X, Y, Z components from the reading and print them out.
               accel_x, accel_y, accel_z = accel
               mag_x, mag_y, mag_z = mag

               # change in x and z values
               a = direction(x)
               b = direction(height)
    
               # "Graphing" the x values by drawing circles/plotting point every second
               draw.ellipse((x+a, top+b, x+shape_width+a, top+shape_height+b), outline=225, fill=225) # both values
    
    
               # Write readings for x and y
               draw.text((x, bottom-10), f'X: {(round (quotient(accel_x, scale), 2))}',  font=font, fill=255)
               draw.text((x+60, bottom-10), f'Z: {(round (quotient(accel_z, scale1), 2))}', font=font, fill=255)
               # Display image.
               disp.image(image)
               disp.display()
               # clear just the bottom leaving the points there to look at
               draw.rectangle((0,bottom-20,width,bottom), outline=0, fill=0)
        
               with PiCamera() as camera: 
                   camera.start_preview()
                   camera.capture('/home/pi/Documents/Pi_in_the_Sky/pics/____-%s.jpg' % frame) # adding numbers to pictures *put date where ____ is
                   frame += 1
                   sleep(.5)
               if input_state1 == False: 
                     print('right button was pressed!')
                     break

finally:
    GPIO.cleanup()  
```
### What needs to be changed/improved? 
### Pictures 
##### Of plane 
##### From flight
