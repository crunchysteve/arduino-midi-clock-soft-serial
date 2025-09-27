# Arduino MIDI clock with tap tempo

### Forker's Note
*A fork that has been modified to use SoftwareSerial.h, allowing it to run on Arduino Uno or Nano and still 
allowing a debug console. MIDI In/Out are on Serial1, attached to pins 6 and 7, respectively. This modification 
is not yet hardware tested but does compile without error, so have at iit. I'm also contemplating adding a 
rotary encoder in parallel with tap tempo for specific tempo setting. I'm also considering upgrading the display 
to an old LCD128x64 display I have left over from a dead Tronxy 3D printer. This has an SD card slot that could be 
used as a MIDI logger/recorder by looping the MIDI out from the last device back to the clock's input. This last 
feature may just be scope creep, so no promises there.*

**Italics below** *indicate changes I'll be making or are already made.*

### ~~&nbsp;Original&nbsp;~~ Readme (now with mods)
As seen on LittleBits:
https://classroom.littlebits.com/inventions/littlebits-arduino-midi-master-clock-with-tap-tempo

You can also do this with a regular Arduino, but you'll have some extra work soldering the button(s)/dimmer

## How to make a Arduino MIDI connector
See the excellent tutorial at this link:
http://www.instructables.com/id/Send-and-Receive-MIDI-with-Arduino/step3/Send-MIDI-Messages-with-Arduino-Hardware/ .

Or check the electrical spec here:
https://www.midi.org/articles/midi-electrical-specifications

## Connections

### For MIDI out

- Connect MIDI ground to Arduino ground
- Connect MIDI 5V to Arduino 5V **with a 220 Ohm resistor in between**
- Connect MIDI signal line to Arduino serial input pin (D1)

### For tap in

Connect a button to D2

## Usage

- Upon startup, Arduino will start sending 100 BPM MIDI clock signal (or last saved BPM value if available).
- Tap the tempo (minimum 3 times)
- After the last tap, clock tempo will be updated and MIDI clock signal will send new BPM

### Features:
- **MIDI clock output** on *pin D7 TX*
- **Tap tempo** input
- **Dimmer input** when a dimmer is connected to A0 to set the tempo by twisting the knob! *(Intention is to change to a rotary encoder.)*
- Tempo blinking **LED** on *pin 13*
- Sync signal on pin 9 (for example to sync with *DIN24/48*...)
- **MIDI real-time start/stop** is sent when button press is detected on A1 port
- **BPM storage in EEPROM** and restores it on power up
- **MIDI forwarding** if a MIDI input is present on *pin D6* RX
- Output of the BPM to a TM1637 **LED display** *(Planning to create some alternate display versions)*

# Branches

- master: Code for the *Arduino Uno/Nano rather than Leonardo*
- arduino-uno: Code for Arduino Uno and compatible devices *(D6/D7 RX/TX pins are used for MIDI in/out, via SoftwareSerial.h, allowing debug console!)*
- For this version, because D6 and D7 are now the MIDI pins, I recommend the Adafruit MIDI featherwing or hardwiring the MIDI circuits for the arduino-uno
- branch. https://learn.adafruit.com/adafruit-midi-featherwing/overview OR https://n-audio.net/designing-midi-in-and-midi-out-schematics/ *

# Enjoy! :)
