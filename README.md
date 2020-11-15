# Marlin 2.0.x ender 3 pro config

https://www.thingiverse.com/thing:3293821

1. Open up Marlin on Arduino IDE. - Check out this video - for more info. 
2. Enable or change these settings in **Configuration.h** 
`#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN`
`#define Z_ENDSTOP_SERVO_NR 0` => Z_PROBE_SERVO
`#define Z_SERVO_ANGLES {174,45}`
`#define Z_HOMING_HEIGHT 2`
`#define Z_CLEARANCE_DEPLOY_PROBE 6`
`#define Z_CLEARANCE_BETWEEN_PROBES 6`
`#define Z_MIN_PROBE_REPEATABILITY_TEST`
`#define AUTO_BED_LEVELING_BILINEAR`
`#define EXTRAPOLATE_BEYOND_GRID`
`#define Z_SAFE_HOMING`
`#define HOMING_FEEDRATE_Z (6*60)`
`#define SERVO_DELAY { 1000 }`
`#define DEACTIVATE_SERVOS_AFTER_MOVE`

3. Set up the offset
=> now nozzle_to_probe_offset
`#define X_PROBE_OFFSET_FROM_EXTRUDER -36 // X offset: -left +right [of the nozzle]`
`#define Y_PROBE_OFFSET_FROM_EXTRUDER -5 // Y offset: -front +behind [the nozzle]`
`#define Z_PROBE_OFFSET_FROM_EXTRUDER 0 // Z offset: -below +above [the nozzle]`

4. Select Servo pin, under the Servo section in **Configuration.h** add this.
For **Pin 27** (using Pin 27 adapter or cutting the lcd wire) `#define SERVO0_PIN 27`
`#define NUM_SERVOS 1` 

For **Pin 29** (soldering the servo wire to the board)
`#define SERVO0_PIN 29`
`#define NUM_SERVOS 1`

5. Set the invert for micro switch to true, since we wire the switch normally closed.
`#define Z_MIN_ENDSTOP_INVERTING true // set to true to`
`#define Z_MIN_PROBE_ENDSTOP_INVERTING true // set to true to invert the logic of the probe.`

6. if you compile the sketch, you will get an error as the 1248p got not enough space. So you need to disable the following features by commenting it out. (//)

**Configuration.h**
`//#define SHOW_BOOTSCREEN`
`//enable this to gain some space.`
`#define SLIM_LCD_MENUS` 

**Configuartion_adv.h**
`//#define ARC_SUPPORT // Disable this feature to save ~3226 bytes`
7. Compile the sketch and Upload the firmware.
8. Turn off the printer.