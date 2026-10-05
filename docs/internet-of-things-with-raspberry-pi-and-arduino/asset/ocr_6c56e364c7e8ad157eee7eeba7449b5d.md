```
elif ir1_state == True and ir2_state == False:
nM11_pin.write(0) # make pin5 to LOW
M12_pin.write(0) # make pin4 to LOW
M21_pin.write(1) # make pin3 to HIGH
M22_pin.write(0) # make pin2 to LOW
print('Right') # print on terminal
time.sleep(0.5) # delay of 500mSec
elif ir1_state == True and ir2_state == True:
M11_pin.write(0) # make pin5 to LOW
M12_pin.write(0) # make pin4 to LOW
M21_pin.write(0) # make pin3 to LOW
M22_pin.write(0) # make pin2 to LOW
print('Stop') # print on terminal
time.sleep(0.5) # delay of 500mSec
```