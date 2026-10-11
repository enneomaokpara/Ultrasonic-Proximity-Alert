# Ultrasonic-Proximity-Alert
A distance-based alert system modeled on car parking sensors: an HC-SR04 ultrasonic sensor measures distance and drives a three-zone LED alert - green (clear), yellow (caution), flashing red (danger).
**Status:** Designed, wired, and validated in simulation (Tinkercad Circuits). 
## How it works
The HC-SR04 fires an ultrasonic ping and times the echo. Distance = (echo time × speed of sound) / 2.
<img width="1206" height="722" alt="image" src="https://github.com/user-attachments/assets/bb719ab5-b7ec-459b-93a8-9a78a9bc3ef7" />
Serial Monitor streams live distance readings for debugging.
## Design decisions
- **No buzzer:** the kit had no buzzer, so the danger zone uses a flashing red LED instead of an audible alarm. Same information, zero extra parts.
- **220 S resistors** on each LED cathode for current limiting.
- **Thresholds (10/25/50 cm)** chosen to give three visually distinct zones within the sensor's reliable indoor range.
## Build log
1. **Physical build (breadboard + Elegoo Uno
R3) :** HC-SR04 VCC>5V, GND>GND, TRIG>D9,
ECHO→D10. LEDs green→D5, yellow>D, red→D7 (anodes); each cathode through a 220 S resistor to GND. Fully wired; upload blocked by a dead USB cable (replacement pending).
2. **Simulation (Tinkercad Circuits):** rebuilt the identical circuit virtually - Uno
R3, HC-SR04, 3 LEDs, 3x 220 2 resistors, same code.
## Validation (Tinkercad)
Dragged the sensor's distance slider through all three zones:
<img width="1206" height="526" alt="image" src="https://github.com/user-attachments/assets/c83c4033-902f-4807-8af6-bd6ae5797dd2" />
All three thresholds trigger in the correct zones. Distances in inches convert cleanly to
the cm thresholds in code (2.9 in = 7.4 cm <
10 cm, etc.).
## Documents
1. **Circuit overview** - full Tinkercad wiring view 
2. **Each alert state** - simulation running with green lit, yellow lit, red lit (3 shots).
3. **Code** 
4. **Serial output** - distance readings streaming while the slider moves.
5. **Physical build photo** - the wired breadboard.
## Expected vs. actual
**Expected:** three clean distance zones driving three LEDs, physical build uploads and works on the first try.
**Actual:**
- The smart-car shield's male header pins were incompatible with male-to-male jumpers, so the shield came off and the sensor + LEDs were wired directly to the bare Uno's female headers instead. Fewer obstacles, full pin access.
- The USB cable died before the sketch could be uploaded - the physical build is fully wired but untested. (Replacement cable pending.)
- The Tinkercad rebuild worked exactly as designed on the first simulation run: all three zones triggered at the right thresholds (see validation table above).
- One self-caught mistake: initially grabbed the 3-pin PING))) sensor in Tinkercad instead of the 4-pin HC-SR04 - caught by checking the pin labels before wiring.
- ## Honest scope
Designed and simulation-validated by Emmanuella Okpara. 
The physical build is wired but not yet upload-tested (USB cable failure).
