# One_Month_Check_In
This update is from March 1 (a month after the project has started)
## What have we done?

### Design/Cut

In this month we have made a design for the plane and have printed mutiple to test the flight capability of it. There has been a total of 3 versions of the plane that change size, center of gravity points, and angles of wings. 

### Coding/Wiring

we have also finished most of the code other than a few things. The lights have been figured out, the accelerometer/OLED screen is done, and most of the iring is pretty final. So far we have been able to stay mostly on schedule, but we have run into a few bumps where we had to spend an extra bit of time on some things. We have found multiple helpful websites that have helped along the way.

## What still need to be done?

### Design/Cut

Design stuff

### Coding/Wiring

A few tasks still need to be done befre we can move onto the testing and refining stages of the project. On the coding/wiring side of things, the code working together and without being attached to a computer still needs to be figured out. Making it battery operated and soldering pieces together also needs to be completed within the next few weeks.

## Where are we struggling?

### Design/Cut

The planes keep flipping going front first. There was too much weight in the front, so we changed the design. We are trying to distribute the weight evenly, but without the pi and everything inside, it is a bit difficult to gage. We are waiting to change it anymore until we are able to test everything together for the first time.

### Coding/Wiring

The pi camera gave us a lot of trouble. I tried many different ways and still have not settled on a particular one. 

## What has been changed?

### Design/Cut

The plane is no longer closed, rather it is two sides with an open middle. It is also going to be made only out of cardboard to improve durability and weight. The wings have also changed a lot. There are now two sets of wings. In the final design (for now) both set of wings are curved and angled. 

### Coding/Wiring

We are no longer going to be dropping things from the plane. There will only be lights as of right now. We got rid of the things falling to get rid of some of the weight and in the interest of time. We could possibly add this or another thing back to the project if time allows. 

## Bill of Materials
- LSM303
- OLED Display
- Pi Camera
- 2 Buttons
- 6 LEDS
- Switch
- Rubberband

Materials
- Cardboard

## Pictures/Diagrams

### Design/Cut

Link to Onshape Document: https://cvilleschools.onshape.com/documents/492561168bf6b91a97d77a47/w/45d7efb3da141b22b711ac96/e/4b3a4ccdc809ca3a080ae7f4

#### In Onshape

#### Version 3 (Final as of right now)

![Screenshot 2022-03-03 9 52 52 AM](https://user-images.githubusercontent.com/60272021/156589460-5ff91dea-edbb-4563-aca9-adfe65bd77a1.png)

#### Laser Cut

##### Version 1

![Screenshot 2022-03-03 9 59 49 AM](https://user-images.githubusercontent.com/60272021/156590828-7085db7d-46a6-4710-9ebc-519f81f610b8.png)

##### Version 2 - Added a second set of wings

![Screenshot 2022-03-03 10 00 05 AM](https://user-images.githubusercontent.com/60272021/156590900-1bf0d4be-968a-4302-82c7-9ed34e270bba.png)

##### Final Printed - Angled and curved wings

![Screenshot 2022-03-03 10 24 57 AM](https://user-images.githubusercontent.com/60272021/156595463-9ebacbb5-0c09-4814-a178-cf23a2143108.png)

### Coding/Wiring

### Wiring - Better pictures/diagrams will come

![Screenshot 2022-03-03 9 36 39 AM](https://user-images.githubusercontent.com/60272021/156586159-3fd2d8d5-d540-4465-90f7-1111caf976b9.png)

#### Code snipets

##### Accelerometer/OLED Screen
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
##### Pi Camera
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
##### LEDS
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
