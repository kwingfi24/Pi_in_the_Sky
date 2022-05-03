# Test_1
Ready to fly on March ___
## How did it go?
## What worked and what didn't?
#### Code: 
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
                   camera.capture('/home/pi/Documents/Pi_in_the_Sky/pics/Mar22-%s.jpg' % frame) # adding numbers to pictures
                   frame += 1
                   sleep(.5)
               if input_state1 == False: 
                     print('right button was pressed!')
                     break

finally:
    GPIO.cleanup()  
```
## What needs to be changed/improved? 
## Pictures 
#### Of plane 
#### From flight