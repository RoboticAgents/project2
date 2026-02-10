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
