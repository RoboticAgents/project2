# Project 2: Introduction to Programmable Logic Controllers (PLC)

**Due:** February 23 at 11:50 AM  
**Location:** Bessemer (LearnLab PLC Training Systems)

---

## Timeline

- **Assigned:** February 10, 2026
- **Lab Sessions:** 
  - February 10 (2:30-4pm): Lab 0 - Logic operations (AND, OR, XOR)
  - February 17 (2:30-4pm): Parts 1-5 work session
  - February 23 (11-11:50am): Final demonstrations and technical interviews
- **Final Product Due:** February 23 at 11:50 AM
- **Duration:** 2 weeks

---

## Table of Contents

- [Timeline](#timeline)
- [Overview](#overview)
- [Learning Outcomes](#learning-outcomes)
- [Team Structure](#team-structure)
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
- [Team Evaluation Process](#team-evaluation-process)
- [Resources](#resources)
- [Submission Instructions](#submission-instructions)
- [Academic Integrity](#academic-integrity)
- [Getting Help](#getting-help)
- [Safety Notes](#safety-notes)

---

## Overview

In this project, you will work hands-on with an industrial Programmable Logic Controller (PLC) using the Allen-Bradley Micro820. PLCs are used to control real-world systems such as manufacturing equipment, traffic systems, and safety-critical machinery.

**Note:** We have already completed basic logic operations: AND, OR, XOR during our previous lab session.

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

## Team Structure

- **Team Size:** 2–3 students per PLC station
- **Team Formation:** Teams are assigned by the instructor (posted on Discord)
- **Individual Accountability:** Each team member must demonstrate hands-on operation of the PLC at least once and understanding of all parts
- **Rotation Requirement:** During lab sessions, team members should rotate who is actively programming/testing
- **Collaboration:** All team members must contribute to design, programming, testing, and documentation
- **Evaluation:** Individual technical interviews and peer evaluations ensure everyone understands the system

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
- **Add a comment above each rung** explaining what the rung does

### Demonstration Requirements

You must show:
1. Green button turning the green light ON and keeping it ON (even after release)
2. Red button turning the green light OFF
3. Explain how the latching circuit maintains state
4. **Create a condition table in your reflection** for each rung showing when the output is TRUE

**Example condition table format:**
```
Rung | Purpose              | Conditions for Output = TRUE
-----|----------------------|--------------------------------
1    | Example output       | Input A is pressed AND Input B is NOT pressed
2    | Another output       | Timer has finished OR Input C is TRUE
```

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
- **Add a comment above each rung** explaining what the rung does

### Demonstration Requirements

You must show:
1. Red light ON in default state (no button pressed)
2. Red light OFF when green button is held down
3. Red light returns to ON when green button is released
4. Explain the difference between normally open (NO) and normally closed (NC) contacts
5. **Create a condition table in your reflection** for each rung showing when the output is TRUE

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
- Change the timer duration 
- Add logic so both red and green lights are OFF during the siren phase
- Add a second timer for a multi-stage warning system
- Make the siren pulse (on/off) during the warning period instead of continuous

**Important:** Add a comment above each rung explaining what the rung does and how it contributes to the sequence.

### Demonstration Requirements

You must show:
1. System idle with red light ON
2. Green button starting the sequence
3. Siren sounding for the timer duration
4. Green light coming ON after timer finishes
5. Red button resetting the system
6. Explain your modification and why you implemented it that way
7. **Create a condition table in your reflection** for each rung showing when outputs turn ON based on timer state and input conditions

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
- Make the lights have different ON durations
- Add the buzzer to sound only during transitions
- Create a three-phase pattern (green, red, both OFF, repeat)
- Add start/stop control using the green and red buttons

**Important:** Add a comment above each rung explaining what the rung does and how the timers interact.

### Demonstration Requirements

You must show:
1. Continuous alternating behavior
2. Consistent timing
3. Your modification working correctly
4. Explain how the timers interact with each other
5. **Create a condition table in your reflection** for each rung describing what enables each timer and what each timer controls

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

**Important:** Add a comment above each rung explaining what the rung does and which step it controls.

### Demonstration Requirements

You must show:
1. System idle (both limit switches not activated)
2. Activating DI_02 and showing Step 1 complete
3. Activating DI_03 and showing Step 2 complete
4. System locked out until reset
5. Red button resetting the system
6. Your modification working correctly
7. Explain how sequential logic differs from parallel logic
8. **Create a condition table in your reflection** for each step showing what conditions must be TRUE for that step to activate

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

2. **PLC Programs** (choose one option):
   - **Option A:** Export and upload your CCW program file (.ACD file) for each part (Part1.ACD, Part2.ACD, etc.)
   - **Option B:** Submit screenshots of ladder logic for each part:
     - Part 1 ladder logic
     - Part 2 ladder logic
     - Part 3 ladder logic (showing timer and master bit)
     - Part 4 ladder logic (showing multiple timers)
     - Part 5 ladder logic (showing limit switches and step bits)
   - Additionally, include at least two screenshots of live I/O or timer status during operation

3. **In-lab demonstration**:
   - **Team demonstration:** Show working behavior for all five parts to the instructor
   - **Individual operation requirement:** Each team member must personally operate the PLC to demonstrate at least one part during the team demo
   - Be prepared to explain your modifications and logic choices

4. **Peer and self-evaluation form** (due with final submission):
   - Complete [peer and self-evaluation form](https://forms.gle/PLACEHOLDER) for each teammate
   - Rate contributions, collaboration, and reliability

## Assessment

**Total: 10 points** (part of 40 points for all projects)

**Your grade = (Team Product Score + Technical Interview Score) − Contribution Penalty**

### Team Product Evaluation (7.5 points)

All team members start with the same team product score.

#### Functionality (6.0 points)
- [ ] Part 1: Latching control with memory (1.0 pt)
- [ ] Part 2: Inverse logic with NC contacts (1.0 pt)
- [ ] Part 3: Timer-based sequential control + modification (2.0 pts)
- [ ] Part 4: Multiple timers and alternating behavior + modification (2.0 pts)
- [ ] Part 5: Sequential logic with limit switches + modification (1.5 pts)

#### Documentation (1.5 points)
- [ ] Condition tables completed for all parts (0.6 pts)
- [ ] Reflection quality and insights (0.6 pts)
- [ ] Program files or screenshots with comments (0.3 pts)

### Individual Technical Interview (2.5 points)

Each student will have a ~5 minute individual meeting with the instructor (during February 23 session or immediately after) where you will:
- **Demonstrate operation:** Run one assigned part on the PLC (chosen by instructor)
- **Explain ladder logic:** Walk through your condition table and explain when outputs turn ON/OFF
- **Describe modifications:** Explain the modifications your team made to Parts 3-5
- **Answer conceptual questions:** 
  - What is the difference between NO and NC contacts?
  - How does a timer work in ladder logic?
  - When would you use a PLC vs a microcontroller?
  - How does memory/latching differ from direct control?

**Scoring:**
- **2.25–2.5 pts:** Can operate PLC confidently, explain all logic clearly, deep understanding
- **1.9–2.2 pts:** Can operate PLC, explain most concepts, solid understanding
- **1.5–1.8 pts:** Basic operation ability, some gaps in explanation
- **1.0–1.4 pts:** Struggles with operation or cannot explain logic adequately
- **0–0.9 pts:** Cannot operate PLC or demonstrate minimal understanding

### Peer Evaluation & Contribution Penalty (0 to −10 points)

After calculating your base score (Team Product + Technical Interview = up to 10 points), a penalty is applied based on peer evaluations and contribution evidence.

**Penalty determined by:**
- Peer evaluation feedback (communication, collaboration, hands-on participation, contribution quality)
- Observation during lab sessions (did you actively program/test or just watch?)
- Self-reflection quality and alignment with peer feedback

**Penalty levels:**
- **No penalty (0 pts deducted):** Excellent peer reviews (4.5–5.0 avg), strong evidence of hands-on participation
- **Minor penalty (−0.5 to −1 pts):** Good peer reviews (3.5–4.4 avg), minor contribution concerns
- **Moderate penalty (−1.5 to −3 pts):** Adequate peer reviews (2.5–3.4 avg), limited hands-on participation
- **Major penalty (−4 to −7 pts):** Poor peer reviews (1.5–2.4 avg), minimal hands-on work
- **Severe penalty (−8 to −10 pts):** Very poor peer reviews (<1.5 avg), non-participation

### Extra Credit (up to 0.5 points)
- Advanced modifications beyond requirements (e.g., counters, complex multi-timer sequences, advanced interlocks) (0.3 pts)
- Exceptional documentation, innovation, or demonstrating deep PLC understanding (0.2 pts)

---

## Team Evaluation Process

### Peer and Self-Evaluation Form (Due February 23)

Each team member will complete a **peer and self-evaluation form** (Google Form) that includes:

**Part 1: Peer Evaluation**

For each teammate (including yourself), rate on a scale of 1-5:

1. **Communication:** Did they communicate actively and keep the team updated?
2. **Hands-on Participation:** Did they actively program/test the PLC or just observe?
3. **Work Quality:** Did they put in genuine effort to understand and document the logic?
4. **Collaboration:** Were they open to discussion and willing to help debug?
5. **Contribution:** Did they contribute an equal/fair share to programming and testing?
6. **Reliability:** Did they attend all sessions and follow through on commitments?

**Open-ended questions:**
- Describe specific tasks this teammate completed
- Would you want to work with this teammate again? Why or why not?

**Part 2: Self-Reflection**

**Your Contributions:**
- List which parts you personally programmed/tested
- Estimate hours spent on the project
- Were there any circumstances that affected your ability to contribute?

**Honest Assessment:**
- Rate your own communication, hands-on participation, work quality, collaboration, contribution, and reliability (1-5)

---

## Resources

### PLC Documentation
- [Allen-Bradley Micro800 Programming Guide](https://literature.rockwellautomation.com/idc/groups/literature/documents/um/2080-um002_-en-e.pdf)
- [Connected Components Workbench User Manual](https://literature.rockwellautomation.com/idc/groups/literature/documents/um/ccw-um001_-en-p.pdf)
- [PLC Guidebook Parts II and III](https://drive.google.com/file/d/1gDMwGD6chMFH_-qLaJD7Ft-CEAc2gAlF/view?usp=sharing)

### Ladder Logic Tutorials
- [Introduction to Ladder Logic](https://www.plcacademy.com/ladder-logic-tutorial/)
- [Understanding PLC Timers](https://instrumentationtools.com/plc-timer-instructions/)
- [Ladder Logic Basics - Video Series](https://www.youtube.com/playlist?list=PLd7Qhmq_dP0NzSJ6mXj2N5p9HFq9YvKBR)

### Reference Materials
- Class lecture slides and notes
- [Step-by-step slide presentation](https://docs.google.com/presentation/d/17-4WhA_WngpMENG631DXtnen3qnBNmOJ/edit?usp=sharing&ouid=115017904697304329138&rtpof=true&sd=true)

### Industrial Control Concepts
- *Introduction to Autonomous Robots* (Correll et al.) - Chapter on Control Systems
- [PLCs in Industry - Applications](https://www.automationdirect.com/plc-applications)

---

## Submission Instructions

### Deadlines
Submit via your team's GitHub repository:
- **February 23, by 11:50 AM:** Push all deliverables:
  - Reflection document to `writing/reflection.md`
  - PLC program files (.ACD) OR screenshots to `programs/` or `photos/` folder
  - Any additional documentation

**Additionally, by February 23 at 11:50 AM each team member must complete:**
- [Peer and self-evaluation form](https://forms.gle/PLACEHOLDER)

### What to Submit

1. **GitHub Repository Contents:**
   - `writing/reflection.md` - completed with all sections and condition tables
   - `programs/` folder - CCW program files for each part (Part1.ACD, Part2.ACD, etc.) **OR**
   - `photos/` folder - screenshots of ladder logic for each part
   - `photos/` folder - at least 2 screenshots of live I/O or timer status during operation

2. **Google Form:**
   - Complete peer and self-evaluation form (link provided above)

### Lab Demonstration (February 23)
- Arrive at Bessemer by 11:00 AM
- Be prepared to demonstrate all five parts
- Each team member must personally operate the PLC for at least one part
- Technical interviews will occur during or immediately after demonstrations

---

## Academic Integrity

- **Collaboration:** You may discuss concepts with other teams, but your ladder logic programs must be your own team's work
- **Resources:** Cite any external tutorials, websites, or documentation you reference in your reflection
- **LLM Usage:** If you use ChatGPT, Copilot, or other AI tools:
  - Document what you asked and how you used the responses in your reflection
  - You must understand and be able to explain any code/logic generated
  - You are responsible for correctness and functionality
- **Guidebook:** You may use the PLC Guidebook as a reference, but adapt examples to our I/O mapping
- **Plagiarism:** Copying ladder logic or documentation from other teams is prohibited

---

## Getting Help

- **Lab Sessions:** Use the February 17 lab session to work with your team and get real-time help from the instructor
- **Office Hours:** See course syllabus for office hours schedule
- **Debugging Tips:** 
  - Use CCW's live monitoring to watch inputs and outputs in real-time
  - Test each rung individually before combining logic
  - Document your issue before asking for help (what you expected vs. what happened)
- **Hardware Issues:** If buttons, lights, or the PLC are not responding correctly, notify the instructor immediately
- **Discord:** Post general questions (not solutions) in the project channel

---

## Safety Notes

- Do not modify power wiring without approval
- Power down before changing wiring
- Avoid shorting 24 VDC terminals
- Treat the PLC as industrial equipment
