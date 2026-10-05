# Basics of Raspberry Pi

# 5.19.3 Recipe without Library

```
import RPi.GPIO as RAJ
import time as wait
RAJ_LCD_RS = 26 # RS pin of LCD
RAJ_LCD_E = 19 # E pin of LCD
RAJ_LCD_D4 = 13 # D4 pin of LCD
RAJ_LCD_D5 = 6 # D5 pin of LCD
RAJ_LCD_D6 = 5 # D6 pin of LCD
RAJ_LCD_D7 = 21 # D7 pin of LCD
RAJ_LCD_WIDTH = 16 # total char 16
RAJ_LCD_CHR = True # assign Boolean
RAJ_LCD_CMD = False # assign Boolean
RAJ_LCD_LINE_1 = 0x80 RAM address of LCD for first line
RAJ_LCD_LINE_2 = 0xC0 RAM address of LCD for second line
RAJ_E_PULSE = 0.0005 # give time clear
RAJ_E_DELAY = 0.0005 # give time clear
```

```
def main():
    RAJ.setwarnings(False) # remove the warnings
    RAJ.setmode(RAJ.BCM) # Use BCM GPIO numbers
    RAJ.setup(RAJ_LCD_E, RAJ.OUT) # setup RS pin as output
    RAJ.setup(RAJ_LCD_RS, RAJ.OUT) # setup RS pin as output
    RAJ.setup(RAJ_LCD_D4, RAJ.OUT) # setup D4 pin as output
    RAJ.setup(RAJ_LCD_D5, RAJ.OUT) # setup D5 pin as output
    RAJ.setup(RAJ_LCD_D6, RAJ.OUT) # setup D6 pin as output
    RAJ.setup(RAJ_LCD_D7, RAJ.OUT) # setup D7 pin as output
    RAJ_lcd_init() # initialise LCD
    while True:
        RAJ_lcd_string("R String ",LCD_LINE_1") # print text to ROW 1
        of LCD
        RAJ_lcd_string(" Presents","LCD_LINE_2") # print text to ROW2
        of LCD
        wait.sleep(3) # delay of 3 Sec
        RAJ_lcd_string("123456789012345",LCD_LINE_1")
        RAJ_lcd_string("ABCDEFGHIJK",LCD_LINE_2")
        wait.sleep(3)\# # delay of 3 Sec
```