#include <Adafruit_NeoPixel.h>
#ifdef __AVR__
#include <avr/power.h>
#endif

int const NUM_PIXELS = 12;
int8_t const PIN= 13;
Adafruit_NeoPixel strip;

void steup() {
  strip = Adafruit_NeoPixel(NUM_PIXELS, PIN, NEO_GRB+NEO_KHZ800);
  strip.begin(); 
  strip.show(); // Init all pixels to "off"

  pinMode(2, INPUT_PULLUP);
}

void loop() {
 // Colors are defined in 0xRRGGBB format.
 int sensorValue = digitalRead(2);
 if (sensorValue == 0) {
  strip.setPixelColor(0, 0x400000);
 } else { 
  strip.setPixelColor(0, 0x004000);
 }
 strip.show();
}
