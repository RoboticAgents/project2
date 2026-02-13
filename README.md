# Project 2: Introduction to Programmable Logic Controllers (PLC)

**Due:** February 23 at 11:50 AM  
**Location:** Bessemer (LearnLab PLC Training Systems)

---

## Table of Contents

- [Overview](#overview)
- [Learning Outcomes](#learning-outcomes)
- [Hardware and Software](#hardware-and-software)
- [I/O Mapping for Our Setup](#io-mapping-for-our-setup)
- [Project Structure](#project-structure)
- [Part 1: Direct Control (Green Button Controls Green Light)](#part-1-direct-control-green-button-controls-green-light)
- [Part 2: Inverse Logic (Red Light ON When Green Not Pressed)](#part-2-inverse-logic-red-light-on-when-green-not-pressed)
- [Part 3: Timer & Buzzer (Manufacturing Warning System)](#part-3-timer--buzzer-manufacturing-warning-system)
- [Part 4: Alternating Lights](#part-4-alternating-lights)
- [Part 5: Conveyor System (Limit Switches)](#part-5-conveyor-system-limit-switches)
- [Deliverables](#deliverables)
- [Assessment](#assessment)
- [Safety Notes](#safety-notes)

---

## Overview

In this project, you will work hands-on with an industrial Programmable Logic Controller (PLC) using the Allen-Bradley Micro820. PLCs are used to control real-world systems such as manufacturing equipment, traffic systems, and safety-critical machinery.

**Note:** We have already completed Lab 0 (basic logic operations: AND, OR, XOR) and Lab 1 in class as exercises.

You will now complete **five parts** that build progressively:
- Part 1: Direct input/output control (Green button controls green light)
- Part 2: Inverse logic (Red light ON when green button NOT pressed)
- Part 3: Timer & Buzzer (Manufacturing warning system)
- Part 4: Alternating lights with multiple timers
- Part 5: Conveyor system simulation with limit switches

**Important:** Follow the step-by-step instructions in [this slide presentation](https://docs.google.com/presentation/d/17-4WhA_WngpMENG631DXtnen3qnBNmOJ/edit?usp=sharing&ouid=115017904697304329138&rtpof=true&sd=true) rather than the guidebook, as the guidebook uses different I/O numbers than our wiring setup. For Parts 3-5, you will need to make slight modifications to the basic implementations shown in the slides.

**Critical Attendance Requirement:**

⚠️ **All team members must attend ALL PLC sessions at Bessemer.** If any team member misses even a single PLC session, that student must complete the entire project individually, even if they participated in other sessions.

PLC sessions include:
- February 10 (2:30-4pm): initial exercise
- February 17 (2:30-4pm)
- February 23 (11-11:50am) 

## Learning Outcomes

By completing this project, you will be able to:

1. **Identify** components of a PLC system and associate each with its control function  
   *Fulfills Course Learning Outcome 1*
2. **Implement** basic logic operations (AND, OR, XOR) using ladder logic contacts  
   *Fulfills Course Learning Outcome 2*
3. **Design and test** control programs for direct I/O, memory-based, and timer-based behaviors  
   *Fulfills Course Learning Outcome 2*
4. **Apply** principles of deterministic control and safety interlocks to physical systems  
   *Fulfills Course Learning Outcome 4*
5. **Debug** PLC programs using live I/O monitoring and systematic testing  
   *Fulfills Course Learning Outcome 2*
6. **Explain** the role of PLCs in industrial automation and safety-critical systems  
   *Fulfills Course Learning Outcome 5*
7. **Document** control logic decisions, testing procedures, and system behavior  
   *Fulfills Course Learning Outcome 2*

## Hardware and Software

### Hardware
- Allen-Bradley Micro850 PLC (2080-LC20-20QWB)
- LearnLab training system with:
  - Green and red pushbuttons
  - Green and red indicator lights
  - Buzzer
  - 24 VDC power supply

### Software
- Connected Components Workbench (CCW)
- Ladder Logic programming environment

## I/O Mapping for Our Setup

Use **this mapping**, even if it differs from the guidebook.

### Inputs
- **DI_00** → Green pushbutton  
- **DI_01** → Red pushbutton  
- **DI_02** → Limit Switch 1 (used in Part 5)
- **DI_03** → Limit Switch 2 (used in Part 5)

### Outputs
- **DO_00** → Green light  
- **DO_01** → Red light  
- **DO_03** → Buzzer/Siren  

## Project Structure

You will complete **five parts**. Each part builds on previous concepts and introduces new control logic principles.

Follow the slide presentation for step-by-step guidance, and verify physical behavior at each step before moving on.

## Part 1: Direct Control (Green Button Controls Green Light)

### Purpose

This part demonstrates **direct cause-and-effect** between inputs and outputs using memory/latching logic.

### Requirements

- When you push the green button, the green light turns ON and **stays ON** (latched)
- When you push the red button, the green light turns OFF
- The system remembers its state (uses memory)

### Implementation Notes

- This corresponds to Lab 2 in the guidebook
- Follow the slide presentation for step-by-step instructions
- Use latching logic (output coil drives itself through normally open contact)
- Red button acts as a reset

### Demonstration Requirements

You must show:
1. Green button turning the green light ON and keeping it ON (even after release)
2. Red button turning the green light OFF
3. Explain how the latching circuit maintains state

## Part 2: Inverse Logic (Red Light ON When Green Not Pressed)

### Purpose

This part introduces **inverse logic** using normally closed contacts.

### Requirements

- The red light is ON when the green button is **NOT** pressed
- When the green button is pressed, the red light turns OFF

### Implementation Notes

- This corresponds to Lab 3 in the guidebook
- Follow the slide presentation for step-by-step instructions
- Use a normally closed (NC) contact for the green button
- This demonstrates continuous monitoring of input state

### Demonstration Requirements

You must show:
1. Red light ON in default state (no button pressed)
2. Red light OFF when green button is held down
3. Red light returns to ON when green button is released4. Explain the difference between normally open (NO) and normally closed (NC) contacts

## Part 3: Timer & Buzzer (Manufacturing Warning System)

### Purpose

This part introduces **timers** and simulates a real industrial scenario where equipment gives an audible warning before initiating.

### Problem Scenario

In a manufacturing plant, it is common to give an audible warning when a piece of equipment is about to initiate. You will build a PLC ladder that simulates this scenario.

### Components Used

- **DI_00**: Green button (start)
- **DI_01**: Red button (stop/reset)
- **Master bit**: Internal BOOL for monitoring the system state
- **DO_03**: Siren/Buzzer
- **Timer (TON_1)**: Keep an eye on the output element
- **DO_00**: Green light
- **DO_01**: Red light

### Order of Operations

1. **Current state**: Red light is ON (system idle)
2. **Green button is depressed**: Initiates the sequence
3. **Master bit turns to 1**: Latching the circuit (system active)
4. **Master bit starts a timer**: Timer begins counting
5. **Timer is active**: Siren blows for 5 seconds
6. **Timer times out**: Green light illuminates (system ready)
7. **Red button pressed**: Turns off the green light and resets the system

### Required Modification

You must modify this basic implementation in at least one way. Choose one or more:
- Change the timer duration (e.g., 3 seconds or 10 seconds)
- Add logic so both red and green lights are OFF during the siren phase
- Add a second timer for a multi-stage warning system- Make the siren pulse (on/off) during the warning period instead of continuous

### Demonstration Requirements

You must show:
1. System idle with red light ON
2. Green button starting the sequence
3. Siren sounding for the timer duration
4. Green light coming ON after timer finishes
5. Red button resetting the system
6. Explain your modification and why you implemented it that way

## Part 4: Alternating Lights

### Purpose

This part introduces **multiple timers** working together to create sequential or alternating behavior.

### Requirements

Make the red and green lights alternate ON and OFF:
- Green light ON for X seconds, then OFF
- Red light ON for X seconds, then OFF
- Pattern repeats continuously

### Implementation Notes

- You will need at least two timers
- Each timer controls one light and triggers the other
- The lights should never be ON simultaneously (unless you modify for complexity)
- Consider how timers can enable/reset each other

### Required Modification

You must modify the basic alternating pattern in at least one way. Choose one or more:
- Make the lights have different ON durations (e.g., green 3 sec, red 5 sec)
- Add the buzzer to sound only during transitions
- Create a three-phase pattern (green, red, both OFF, repeat)
- Add start/stop control using the green and red buttons

### Demonstration Requirements

You must show:
1. Continuous alternating behavior
2. Consistent timing
3. Your modification working correctly
4. Explain how the timers interact with each other

## Part 5: Conveyor System (Limit Switches)

### Purpose

This part simulates a **sequential manufacturing process** with multiple stages controlled by limit switches.

### Problem Scenario

You are working at a manufacturing facility that packages products. The first operation involves a box moving down a conveyor belt. There are 2 limit switches (DI_02 and DI_03) that detect the box at different positions. The sequence of events is based on these switches being activated in order.

### Components Used

- **DI_02**: Limit Switch 1 (first position)
- **DI_03**: Limit Switch 2 (second position)
- **DI_01**: Red button (reset)
- **Internal bits**: "Step 1 complete" and "Step 2 complete"
- **DO_00**: Green light (can indicate system state)
- **DO_01**: Red light (can indicate system state)

### Order of Operations

1. **Machine is idle**: DI_02 and DI_03 are not made (not activated)
2. **Box hits DI_02**: This initiates and signals "system ready for DI_03"
3. **When DI_02 is made**: It latches a "Step 1 complete" bit
4. **When DI_03 is made**: It latches a "Step 2 complete" bit (only if Step 1 is already complete)
5. **After DI_03 is made**: The system is done, and a reset is required (Red button, DI_01)

### Required Modification

You must modify this basic implementation in at least one way. Choose one or more:
- Use lights to indicate which step is complete (e.g., green ON after Step 1, red ON after Step 2)
- Add a buzzer that sounds when the sequence is complete
- Prevent DI_03 from being recognized unless DI_02 has already been activated
- Add a timer between steps to simulate processing time
- Create a counter that tracks how many boxes have passed through

### Demonstration Requirements

You must show:
1. System idle (both limit switches not activated)
2. Activating DI_02 and showing Step 1 complete
3. Activating DI_03 and showing Step 2 complete
4. System locked out until reset
5. Red button resetting the system
6. Your modification working correctly
7. Explain how sequential logic differs from parallel logic

---

## Deliverables

Each team must submit:

1. **Short written reflection** (in the reflection.md file):
   - Brief description of what each part demonstrates conceptually:
     - Part 1: Latching and memory
     - Part 2: Inverse logic with NC contacts
     - Part 3: Timer-based sequential control
     - Part 4: Multiple timers and alternating behavior
     - Part 5: Sequential logic with limit switches
   - Describe the modifications you made to Parts 3-5 and why
   - One challenge you encountered and how you resolved it
   - One real-world application where you might use sequential logic like Part 5

2. **Screenshots** (include in your submission):
   - Part 1 ladder logic
   - Part 2 ladder logic
   - Part 3 ladder logic (showing timer and master bit)
   - Part 4 ladder logic (showing multiple timers)
   - Part 5 ladder logic (showing limit switches and step bits)
   - At least two screenshots of live I/O or timer status during operation

3. **In-lab demonstration**:
   - Show working behavior for all five parts to the instructor
   - Be prepared to explain your modifications and logic choices

## Assessment

**Total: 10 points**

- Part 1 functionality (latching control): 1.0 point
- Part 2 functionality (inverse logic): 1.0 point
- Part 3 functionality (timer & warning system) + modification: 2.5 points
- Part 4 functionality (alternating lights) + modification: 2.5 points
- Part 5 functionality (conveyor/limit switches) + modification: 2.0 points
- Documentation and explanation: 1.0 point

Understanding and explanation matter as much as correct behavior.

## Safety Notes

- Do not modify power wiring without approval
- Power down before changing wiring
- Avoid shorting 24 VDC terminals
- Treat the PLC as industrial equipment
