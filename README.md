# Project 2: Introduction to Programmable Logic Controllers (PLC)

**Due:** February 24 at 4:00 PM  
**Location:** Bessemer (LearnLab PLC Training Systems)

---

## Table of Contents

- [Overview](#overview)
- [Learning Outcomes](#learning-outcomes)
- [Hardware and Software](#hardware-and-software)
- [I/O Mapping for Our Setup](#io-mapping-for-our-setup)
- [Project Structure](#project-structure)
- [Lab 2: Direct Control (No Memory)](#lab-2-direct-control-no-memory)
- [Lab 3: Start/Stop Control with Memory](#lab-3-startstop-control-with-memory)
- [Lab 4: Timers and Time-Based Behavior](#lab-4-timers-and-time-based-behavior)
- [Deliverables](#deliverables)
- [Assessment](#assessment)
- [Safety Notes](#safety-notes)

---

## Overview

In this project, you will work hands-on with an industrial Programmable Logic Controller (PLC) using the Allen-Bradley Micro820. PLCs are used to control real-world systems such as manufacturing equipment, traffic systems, and safety-critical machinery.

You will complete **four labs** that build progressively:
- Lab 0: Basic logic operations (AND, OR, XOR)
- Lab 2: Direct input/output control
- Lab 3: Memory and Start/Stop logic
- Lab 4: Time-based control using timers

You will also customize each lab slightly to make the behavior your own and demonstrate understanding.

## Learning Outcomes

By completing this project, you will be able to:

1. Explain what a PLC is and how it differs from a microcontroller
2. Identify digital inputs, outputs, and commons on a PLC
3. Write ladder logic to control physical outputs
4. Implement memory using internal control relays
5. Use timers to create time-based behavior
6. Debug PLC programs using live I/O monitoring
7. Explain system behavior in terms of inputs, logic, and outputs

---

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

---

## I/O Mapping for Our Setup

Use **this mapping**, even if it differs from the guidebook.

### Inputs
- **I-00** → Green pushbutton  
- **I-01** → Red pushbutton  

### Outputs
- **O-00** → Green light  
- **O-01** → Red light  
- **O-02** → Buzzer  

---

## Project Structure

You will complete **four labs**. Each lab has:
- A required base behavior
- A small customization requirement

You should verify physical behavior at each step before moving on.

---

## Lab 0: Logic Fundamentals (AND, OR, XOR)

### Purpose

Lab 0 introduces **basic logic operations** using ladder logic. You will learn how to combine multiple inputs to control outputs using fundamental logic gates.

This is essential for understanding how PLCs process multiple conditions.

---

### Required Behavior

You must implement and demonstrate **all three** of the following logic operations:

#### AND Logic
- **Both** green button (I-00) **AND** red button (I-01) must be pressed  
  → **green light (O-00)** turns ON  
- If either button is released  
  → green light turns OFF

#### OR Logic
- **Either** green button (I-00) **OR** red button (I-01) is pressed  
  → **red light (O-01)** turns ON  
- If both buttons are released  
  → red light turns OFF

#### XOR (Exclusive OR) Logic
- **Exactly one** button is pressed (green **XOR** red)  
  → **buzzer (O-02)** turns ON  
- If both buttons are pressed or both are released  
  → buzzer turns OFF

All three behaviors must work correctly and simultaneously.

---

### Implementation Notes

- Use series contacts for AND logic
- Use parallel contacts for OR logic
- XOR requires a combination: (A AND NOT B) OR (NOT A AND B)
- Test each behavior individually, then verify all three work together

---

### Demonstration Requirements

You must show:
1. AND behavior working (both buttons → green light)
2. OR behavior working (either button → red light)
3. XOR behavior working (exactly one button → buzzer)
4. Explain your ladder logic to the instructor

---

## Lab 2: Direct Control (No Memory)

### Purpose

Lab 2 demonstrates **direct cause-and-effect** between inputs and outputs. There is no memory in the system.

---

### Required Behavior

You should implement and test **both** of the following:

#### Behavior A
- Press and hold **green button (I-00)**  
  → **green light (O-00)** turns ON  
- Release the button  
  → green light turns OFF immediately

#### Behavior B
- Press and hold **red button (I-01)**  
  → **red light (O-01)** turns ON  
- Release the button  
  → red light turns OFF immediately

Outputs must only be ON while the button is physically pressed.

---

### Customization (Required)

Choose **one**:
- Make one button control **two outputs** (for example: light + buzzer)
- Swap which button controls which output
- Add a rung so both buttons control different outputs simultaneously

The behavior must remain **direct** (no latching).

---

## Lab 3: Start/Stop Control with Memory

### Purpose

Lab 3 introduces **memory** using an internal control relay. The PLC now remembers whether the system is ON or OFF.

---

### Required Behavior

- **Green button (I-00)** acts as **Start**
- **Red button (I-01)** acts as **Stop**

Expected behavior:

1. Initially, all outputs are OFF
2. Press and release **Start**
   - System turns ON
3. Outputs remain ON after Start is released
4. Press **Stop**
   - System turns OFF
5. Outputs remain OFF after Stop is released

This requires:
- An internal control relay
- A latching (sealing) contact
- Stop overriding Start

---

### Minimum Output Requirement

When the system is ON, at least **one output** must be active:
- Green light, red light, or buzzer

---

### Customization (Required)

Choose at least **one**:
- Use both lights to indicate system state (for example: green ON when running, red ON when stopped)
- Turn on the buzzer only when the system is ON
- Use two internal relays to control different behaviors

The Start/Stop logic must remain correct.

---

## Lab 4: Timers and Time-Based Behavior

### Purpose

Lab 4 introduces **timers**, allowing the PLC to make decisions based on **elapsed time**, not just button presses.

This is essential for real systems (delays, warnings, sequencing).

---

### Required Behavior (Base)

Use a timer so that **something does not happen immediately**.

Example base behaviors (choose one as your starting point):

- After pressing **Start**, wait a few seconds before turning on an output
- When the system turns ON, activate the buzzer for a short duration
- Delay the red or green light turning ON or OFF

At least **one timer** must be used meaningfully.

---

### Customization (Required)

Choose at least **one** customization:

- Change the timer duration to create a noticeable delay
- Use the timer to create a warning (for example: buzzer turns ON briefly before a light)
- Use a timer to automatically turn something OFF after a set time
- Combine Start/Stop logic with timed behavior

You do **not** need multiple timers unless you want to explore further.

---

### What You Should Observe

- Outputs respond after a delay, not instantly
- Timing behavior is consistent across runs
- Timer behavior is visible in CCW while the program runs

---
## Deliverables

Each team must submit:

1. **Short written reflection** (README or reflection file):
   - What Lab 0 demonstrates about basic logic
   - What Lab 2 demonstrates about direct control
   - What Lab 3 adds conceptually with memory
   - How timers change system behavior in Lab 4
   - One challenge you encountered and how you resolved it

2. **Screenshots**:
   - Lab 0 ladder logic (all three logic operations)
   - Lab 2 ladder logic
   - Lab 3 ladder logic
   - Lab 4 ladder logic (showing timer)
   - At least one screenshot of live I/O or timer status

3. **In-lab demonstration**:
   - Show working behavior for all four labs to the instructor.
   - Show working behavior for all three labs to the instructor.

## Assessment

**Total: 6 points**

- Lab 0 functionality: 1.0 point
- Lab 2 functionality: 1.5 points  
- Lab 3 functionality: 2.0 points  
- Lab 4 functionality: 1.5 points  
- Documentation and explanation: 1.0 point  

Understanding and explanation matter as much as correct behavior.

Understanding and explanation matter as much as correct behavior.

## Safety Notes

- Do not modify power wiring without approval
- Power down before changing wiring
- Avoid shorting 24 VDC terminals
- Treat the PLC as industrial equipment
