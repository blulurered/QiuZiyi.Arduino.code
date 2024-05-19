\#include "Arduino.h"

\#include "LiquidCrystal.h"

**LiquidCrystal** **lcd**(12, 11, 5, 4, 3, 2);

int potPin = A0;    *// Analog pin 0 for the LED brightness potentiometer*

int ledPin = 6;     *// LED Digital Pin with PWM*

int potValue = 0;    *// variable to store the value coming from the potentiometer*

int brightness = 0;   *// converts the potValue into a brightness* 

int pBari = 0;     *// progress bar*

int i = 0;       *// foor loop*

*//progress bar character for brightness*

**byte** pBar[8] = {

 **B11111**,

 **B11111**,

 **B11111**,

 **B11111**,

 **B11111**,

 **B11111**,

 **B11111**,

};

void **setup**() {

 *// setup our led as an OUTPUT*

 **pinMode**(ledPin, **OUTPUT**); 

 *// set up the LCD's number of columns and rows:* 

 lcd.**begin**(16, 2);

 *// Print a message to the LCD*

 lcd.**print**("Hello world!");

 *//Create the progress bar character*

 lcd.**createChar**(0, pBar);

}

void **loop**() {

 *// clears the LCD screen*

 lcd.**clear**();

 *// Print a message to the LCD*

 lcd.**print**("Hello world!");}