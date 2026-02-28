# Simple AM Radio Receiver

## Goal
This was originally a project through university, so the schematic was given. The project however was aiming at making the main circuit without the volume bar and soldering it on a perfboard.

PCB was optional but a great learning curve.

## PCB Design Choices

### Transformer
     The only difference from the intended schematic is the transformer shape. It was meant to be wrapped outside the core and about 6 turns on the primary and 60 on the secondary, however I felt like the loesses would be too great to achieve oscillation at 729kHz with a 30pf-60pf capacitor. Thus I instead did 2 and 21 turns inside the core taking advantage fully of the magnetic flux.
    
    This turned out to be a great decision as we had no amplitude issues when testing.

### Ground plane and Connector location
    A solid ground plane was the best move to keep noise to a minimum with the exception of the area below the inductor, where parasitic capacitance would decalibrate our oscillation. The 2nd layer was also mostly ground for shielding reasons. Finally, the ground connector was placed in the middle in order to essentialy block digital ground (from the LEDs) from reaching the more sensitive signal area.

    In minimal testing this showed up to be a correct decision as grounding from the input area resulted in audible *pops* when the LEDs were switching.

### +V Plane
    At the right side, in the "digital" area, many connectors as well as the LEDs required VCC, this was easily solved by adding a +V plane on the first layer of the PCB, resulting in a low resistance clean path for every component to get power. Signal in that area was not going to be audible and was not sensitive as such, noise reduction was not a number 1 priority.

## Errors

### IC Pin 9
    Due to the +V plane, an island was left that floated and blocked Pin 9 of the LM3915 IC. This was a serious overlook but thankfully not a catastrophic error. The IC pin worked like it was grounded giving a volume "indicator" instead of a full volume bar.

## Improvements

### Size
    Compacting the whole board would be greatly beneficial for size. AF isn't so sensitive so it wouldn't make a big difference but cost would be less.

### Redundancy 
    No need for ground (-) input.

## Overview
    For a first PCB looked pretty good and worked spectacularly.