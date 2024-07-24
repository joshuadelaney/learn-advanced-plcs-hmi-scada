
# Advanced PLCs, HMI & SCADA - Exam Paper - 2019 - Spring

**Instructions**:  Answer question 4 and 5, and any other two questions. All questions carry equal marks.

The use of programmable or text storing calculators is expressly forbidden.

Please note that where a candidate answers more than the required number of questions, the examiner will mark all questions attempted and then select the highest scoring ones.  

## Paper College Details

College: Limerick Institute of Technology  
Module Title: Advanced PLCs, HMI & SCADA  
Module Code: AUTM07018
Year of Study: 3  
Year: 2019 - Spring  
Time Allowed: 2.5 Hours  
File Name: exam-2019-advanced-plcs-hmi-and-scada-autm07018.md

### Programmes

| Code           | Programme                                                  |
|----------------|------------------------------------------------------------|
| LC\_ERENM\_KMY | BEng (Honours) Renewable and Electrical Energy Engineering |
| LC\_ERENM\_JMY | BEng Renewable and Electrical Energy Engineering           |
| LC\_EIARM\_KMY | BEng (Honours) Industrial Automation & Robotic Systems     |
| LC\_EIARM\_JMY | BEng Industrial Automation & Robotic Systems               |
| LC\_EEETM\_KMY | BEng (Honours) Electrical Engineering                      |
| LC\_EEETM\_JMY | BEng Electrical Engineering                                |

### Examiners

| Examiner         |          |
|------------------|----------|
| Ian Foley        | Internal |
| Denis O Meara    | Internal |
| Mr. Mark McGrath | External |

## Question 1 (Total Marks: 25)

### Question 1(a) (5 Marks)

Identify two Rockwell Automation PLC programming software. Describe how the Rockwell Automation Software communicates with PLCs and I/O devices.

#### Question 1(a) Answer

Rockwell Automation has two main PLC programming software:

1. **RSLogix 5000/Studio 5000**: This software is used for programming Rockwell Automation's ControlLogix and CompactLogix family of controllers.
2. **RSLogix 500**: This software is used for programming Rockwell Automation's SLC 500 and MicroLogix family of controllers.

### Question 1(b) (20 Marks)

Explain in detail the operation of the sections of the PLC program shown in **Figure.1**

![Q1b1](images/exam-2019-advanced-plcs-hmi-and-scada-autm07018/figure-1-a.jpeg)

![Q1b2](images/exam-2019-advanced-plcs-hmi-and-scada-autm07018/figure-1-b.jpeg)

![Q1b3](images/exam-2019-advanced-plcs-hmi-and-scada-autm07018/figure-1-c.jpeg)

> Figure.1

#### Question 1(b) Answer

#### Answer:
To explain the operation of the PLC program shown in the provided figures, I will analyze each section of the program based on the images provided.

1. **Figure 1-a**:
   - **Rung 0000**: This rung is controlling the `System R1` relay. The `System R1 Relay Off` condition is checked, and if it is not active (relay is off), the relay is activated. This indicates that the system is initially turned on.
   - **Rung 0001**: This rung controls the `Left Sequence Control` relay. It checks if `SPMA Extend On Lft` is active. If the `SPMA Extend On Lft` is active, it triggers the `Left Lift Down` sequence and the `PMA Start Lft` sequence.
   - **Rung 0002**: This rung continues the `Left Sequence Control`. It checks for `SPMA Extend Out` condition and proceeds to activate the `Left Lift Up Position` when `Left Lift Down` sequence is completed.

2. **Figure 1-b**:
   - **Rung 0003**: This rung handles the `Left Sequence Control`. It checks if `KMC Valve Extend Position` is reached. If true, it continues to `KMC Valve Extend Position`.
   - **Rung 0004**: This rung handles `Left Sequence Control`. It verifies if `PSM Extend On Lft` and `KMC Valve Extend Position` are active. If both conditions are met, the `Left Sequence` relay is triggered to proceed further.
   - **Rung 0005**: This rung handles another section of the `Left Sequence Control`. It checks if `ECM Pusher Retract Position` is active and then sets the `Left Lift Down Position` to proceed to the next step in the sequence.

3. **Figure 1-c**:
   - **Rung 0006**: This rung involves the `Left Sequence Control`. It checks if `ECM Pusher Retract Position` is true, activating the `Left Sequence Control MOP`.
   - **Rung 0007**: This rung checks for `ECM Pusher Retract Position` and if `Left Lift Down Position` is reached, the `Left Sequence Control` is updated accordingly.

Overall, the program handles a sequential control system for a left lift mechanism. The steps involve extending and retracting various components (e.g., `SPMA`, `KMC Valve`, `ECM Pusher`), and moving the lift up and down based on specific position feedback. The sequences are controlled by checking various position sensors and relays to ensure the correct order of operations.

This detailed analysis provides a comprehensive understanding of how the PLC program manages the sequential operations for the lift mechanism.

## Question 2 (Total Marks: 25)

Design a PLC program for a water harvester as outlined below. Create the PLC program using TIA Portal.

![Q2i](images/exam-2019-advanced-plcs-hmi-and-scada-autm07018/question-2.jpeg)

**Operation:**  

An overview of the process is shown above. The process continually maintains a level in the two tanks, which can be taken in or out of service, to supply water to two processes within the plant, rain water supplied to the tanks is collected from factory roof, filtered and stored in an underground storage tank.  

**Automatic mode (auto):**  

Control panel in automatic S3(A), operation started by pressing S2 start and stopped by pressing S1. If the tanks are in service S4(on) tank 1 S5(on) tank 2 and water is available in storage B1on, the process can start filling tanks 1& 2 when called by Level switch B2, B3, B4 and B5.  

**Tank 1 fill-**  

Auto on and tank 1 in service and B1 on and tank 1 calling for water, pump M1 starts and 3 seconds later DV opens, when pump on and DV open V1 opens to allow water into tank 1, tank 1 fills, when level reached B3, V1 off, also DV and Pump M1 if not supplying Tank 2.  

**Tank 2 fill**-  

Auto on and tank 2 in service and B1 on and tank 2 calling for water, pump M1 starts and 3 seconds later DV opens, when pump on and DV open V2 opens to allow water into tank 2 , tank 2 fills when level reached B5, V2 off, also DG and Pump M1 if not supplying Tank 1.  

**Manual mode (Man):**  

Control panel in manual/Hand S3 (H), will allow, via the manual screen on HMI to manually operate the, Valves DV, V1 and V2 at any time to allow for testing/Maintenance of system also to operate pump M1 on condition B1 indicates it’s safe to do so.  

**Safety protection:**  

**Overloads:** Operation of the overload M1, will stop the process, immediately all contactors will be de-energised and Lamp H2 constant, until reset.  

**E/S1:** Operation of the E/S1, will stop the process, immediately all contactors will be de-energised and Lamp H2 Flash, until reset.  

**PLC Tags (Water Harvester)**  

| PLC -Tag         | Data Type | PLC\_Address | NO/NC |
|------------------|-----------|--------------|-------|
| ES1- emergency   | DI-Bool   | I0.0         | 2xNC  |
| stop 1           |           |              |       |
| S1 STOP          | DI-Bool   | I0.1         | NC    |
| S2 START         | DI-Bool   | I0.2         | NO    |
| S3 HAND          | DI-Bool   | I0.3         | NO    |
| S3 AUTO          | DI-Bool   | I0.4         | NO    |
| S4 TANK 1 IN     | DI-Bool   | I0.5         | NO    |
| SERVICE          |           |              |       |
| S5 TANK 2 IN     | DI-Bool   | I0.6         | NO    |
| SERVICE          |           |              |       |
| KM1 AUX          | DI-Bool   | I0.7         | NO    |
| F1 O/L           | DI-Bool   | I1.0         | NO    |
| B1 STORAGE       | DI-Bool   | I1.1         | NO    |
| TANK LOW         |           |              |       |
| B2 TANK 1 LOW    | DI-Bool   | I1.2         | NO    |
| B3 TANK 1 HIGH   | DI-Bool   | I1.3         | NO    |
| B4 TANK 2 LOW    | DI-Bool   | I1.4         | NO    |
| B5 TANK 2 HIGH   | DI-Bool   | I1.5         | NO    |
| PUMP             | DO-Bool   | Q0.0         |       |
| H2 OL/ES         | DO-Bool   | Q0.1         |       |
| H3-DISCHARGE     | DO-Bool   | Q0.2         |       |
| VALVE(DV)        |           |              |       |
| H4- PUMP RUNNING | DO-Bool   | Q0.3         |       |
| H5 -VALVE 1      | DO-Bool   | Q0.4         |       |
| H6-VALVE 2       | DO-Bool   | Q0.5         |       |

### Question 2 Answer

To design a PLC program for the water harvester system using TIA Portal, we need to create a structured program that includes handling automatic and manual modes, ensuring safety protections, and operating valves and pumps based on the specified conditions.

#### Step-by-Step Program Design

##### 1. Define Inputs and Outputs

**Inputs:**

- `ES1`: Emergency Stop (I0.0)
- `S1`: Stop (I0.1)
- `S2`: Start (I0.2)
- `S3`: Hand (Manual Mode) (I0.3)
- `S3`: Auto (Automatic Mode) (I0.4)
- `S4`: Tank 1 in Service (I0.5)
- `S5`: Tank 2 in Service (I0.6)
- `KM1`: Auxiliary (I0.7)
- `F1`: Overload (I1.0)
- `B1`: Storage Tank Low (I1.1)
- `B2`: Tank 1 Low (I1.2)
- `B3`: Tank 1 High (I1.3)
- `B4`: Tank 2 Low (I1.4)
- `B5`: Tank 2 High (I1.5)

**Outputs:**

- `PUMP`: Pump (Q0.0)
- `H2`: Overload/Emergency Stop Indicator (Q0.1)
- `H3`: Discharge Valve (DV) (Q0.2)
- `H4`: Pump Running Indicator (Q0.3)
- `H5`: Valve 1 (Tank 1) (Q0.4)
- `H6`: Valve 2 (Tank 2) (Q0.5)

##### 2. Establish Basic Program Structure

Create networks for initial checks, automatic mode operations, manual mode operations, and safety protections.

##### 3. Implement Safety Protections

Network 1: Emergency Stop (ES1) and Overload (F1)

```ladder
// Emergency Stop and Overload Logic
A I0.0 // ES1 Emergency Stop
A I1.0 // F1 Overload
= Q0.1 // H2 OL/ES Indicator
R Q0.0 // PUMP
R Q0.2 // Discharge Valve (DV)
R Q0.4 // V1
R Q0.5 // V2
```

##### 4. Implement Start/Stop Logic

Network 2: Start and Stop Operations

```ladder
// Start and Stop Logic
A I0.2 // S2 Start
A I0.4 // S3 Auto
= M0.0 // Auto Mode Active

A I0.1 // S1 Stop
= M0.1 // Stop Active

A M0.0
AN M0.1
= M0.2 // System Running
```

##### 5. Automatic Mode Operation

Network 3: Tank 1 Filling Logic

```ladder
// Tank 1 Filling Logic in Auto Mode
A M0.2 // System Running
A I0.5 // Tank 1 in Service
A I1.2 // Tank 1 Low
A I1.1 // Storage Tank has Water
= M0.3 // Start Filling Tank 1

// Start Pump and Open Valves
A M0.3
= Q0.0 // Start Pump
L S5T#3s // 3 Second Timer
A Q0.0 // Pump Running
= Q0.2 // Open Discharge Valve (DV)

A Q0.2
= Q0.4 // Open V1

// Stop Filling Tank 1
A I1.3 // Tank 1 High
= R Q0.4 // Close V1
= R Q0.2 // Close DV
= R Q0.0 // Stop Pump if not filling Tank 2
```

Network 4: Tank 2 Filling Logic

```ladder
// Tank 2 Filling Logic in Auto Mode
A M0.2 // System Running
A I0.6 // Tank 2 in Service
A I1.4 // Tank 2 Low
A I1.1 // Storage Tank has Water
= M0.4 // Start Filling Tank 2

// Start Pump and Open Valves
A M0.4
= Q0.0 // Start Pump
L S5T#3s // 3 Second Timer
A Q0.0 // Pump Running
= Q0.2 // Open DV

A Q0.2
= Q0.5 // Open V2

// Stop Filling Tank 2
A I1.5 // Tank 2 High
= R Q0.5 // Close V2
= R Q0.2 // Close DV
= R Q0.0 // Stop Pump if not filling Tank 1
```

##### 6. Manual Mode Operation

Network 5: Manual Mode Control

```ladder
// Manual Control for Valves and Pump

// Check if the system is in Manual Mode and if the Storage Tank has Water
A I0.3 // Manual Mode (S3 HAND)
A I1.1 // Storage Tank has Water (B1 STORAGE TANK LOW)

// Manual Pump Control
A M0.5 // Manual Start Pump Command
= Q0.0 // Start Pump

// Manual Discharge Valve (DV) Control
A M0.6 // Manual Open DV Command
= Q0.2 // Open DV

// Manual Valve 1 (V1) Control
A M0.7 // Manual Open V1 Command
= Q0.4 // Open V1

// Manual Valve 2 (V2) Control
A M0.8 // Manual Open V2 Command
= Q0.5 // Open V2
```

##### 7. Indicator Lights

Network 6: Indicator Lights

```ladder
// Indicators
A Q0.0 // Start Pump
= Q0.3 // Pump Running

A M0.5
= Q0.4 // V1 Open

A M0.6
= Q0.5 // V2 Open
```

##### Program Summary

- **Safety protections**: Emergency stop and overload conditions immediately stop all operations.
- **Automatic mode**: System automatically fills Tank 1 or Tank 2 when they are low and the storage tank has water, using interlocks and timers for sequential operation.
- **Manual mode**: Allows manual control of the pump and valves for maintenance and testing.
- **Indicator lights**: Provide visual feedback for system status.

This PLC program ensures a robust and reliable control system for the water harvester, capable of handling automatic and manual operations while ensuring safety and efficiency.

## Question 3 (Total Marks: 25)

**Process Description**  

A control system is required to move a part from the ‘Part Pickup Position’ to the ‘Home Position’ once the system is placed in Auto and the Start button is pressed. There are three valves controlling actuators with Reed switches to feedback whether the actuator is extended or retracted. The system configuration is represented by the image below: **Figure.2**

![Figure 2](images/exam-2019-advanced-plcs-hmi-and-scada-autm07018/figure-2.jpeg)

> Figure 2

The sequence is as follows:

Once placed in Auto Mode and the start button is pressed the system will move in a safe manner to the home position. Once a part is detected the positioner will extend, then the part pickup will extend, clamp the part and return to the home position and place the part for collection by the operator.

There are 3 valves controlling actuators with feedback on the cylinders.

<u>Ball Clamp (Inputs)</u>

**Clamp Activated (I40.4)**  
**Clamp Deactivated (I40.3)**  

<u>Ball Clamp (Outputs)</u>

**Activate Clamp (Q50.1)**  

<u>Part Pickup (Inputs)</u>

**Part Pickup Extended (I40.2)**  
**Part Pickup Retracted (I40.1)**  

<u>Part Pickup (Outputs)</u>

**Extend Part Pickup (Q50.0)**  

<u>Positioner (Inputs)</u>

**Positioner Extended (I40.6)**  
**Positioner Retracted (I40.5)**  

Positioner (Outputs)</u>

**Extend Positioner (Q50.3)**  
**Retract Positioner (Q50.2)**  

<u>Interlocks</u>

**Pressure Switch  (I40.7) E-Stop  (I41.6)**  
**Stop Pushbutton  (I41.5) Auto Selector Switch (I50.0) Part Present (I40.0)**  

<u>Sequence Step Value</u>

Sequence Step **(MW100)**  

<u>Operator Interface</u>

1. **Start Pushbutton (I41.3)**  
2. **Stop Pushbutton  (I41.5)**  
3. **Auto Selector Switch (I50.0)**  
4. **Index Pushbutton (I41.4)**  
5. **Reset Pushbutton (I41.2)**  
6. **Lamp Indicator System Running (Q50.5)**  

Sketch and clearly explain a structured programme to implement the application in **Figure.2** above using a Siemens S7 PLC. Create Symbol table for all I/O and internal bits used in the PLC code. **[6 Marks]**

***Operation***  

1. Initialise an Auto Mode to begin Sequence control. (Auto Mode M0.0).
   Activate indicator Lamp for system running. **[3 Marks]**
2. Activate Outputs from Sequence Control. **[4 Marks]**
3. Program Sequence Control and transition to next step when transition interlock is met **[8 Marks]**
4. Reset Sequence when not in Auto and Index Pushbutton is pressed and held for 2 secs **[2 Marks]**
5. After part is placed in the home position ensure that another part is not placed there until the index push has been pressed by the operator to indicate that the part in the home position has been removed. (Part in home position M0.1) **[2 Marks]**

### Question 3 Answer

To design a structured program to implement the described application using a Siemens S7 PLC, we will follow the provided requirements and steps. The program will utilize Ladder Logic and be divided into the specified sections. Let's break down each section and the sequence control logic.

#### Symbol Table

**Inputs:**
| Symbol           | Address | Description                    |
|------------------|---------|--------------------------------|
| AutoMode         | I50.0   | Auto Selector Switch           |
| StartButton      | I41.3   | Start Pushbutton               |
| StopButton       | I41.5   | Stop Pushbutton                |
| EStop            | I41.6   | Emergency Stop                 |
| PressureSwitch   | I40.7   | Pressure Switch                |
| PartPresent      | I40.0   | Part Present                   |
| ClampActivated   | I40.4   | Clamp Activated                |
| ClampDeactivated | I40.3   | Clamp Deactivated              |
| PartPickupExt    | I40.2   | Part Pickup Extended           |
| PartPickupRet    | I40.1   | Part Pickup Retracted          |
| PositionerExt    | I40.6   | Positioner Extended            |
| PositionerRet    | I40.5   | Positioner Retracted           |

**Outputs:**
| Symbol          | Address | Description                    |
|-----------------|---------|--------------------------------|
| SystemRunning   | Q50.5   | Lamp Indicator System Running  |
| ActivateClamp   | Q50.1   | Activate Clamp                 |
| ExtendPartPickup| Q50.0   | Extend Part Pickup             |
| ExtendPositioner| Q50.3   | Extend Positioner              |
| RetractPositioner| Q50.2  | Retract Positioner             |

**Internal Bits:**
| Symbol          | Address | Description                    |
|-----------------|---------|--------------------------------|
| AutoMode        | M0.0    | Auto Mode                      |
| PartInHomePos   | M0.1    | Part in Home Position          |
| SeqStep         | MW100   | Sequence Step                  |

#### Ladder Logic Design

##### 1. Initialize Auto Mode and System Running Lamp

```plaintext
|----[ I50.0 ]------------------------------------------( M0.0 )----|
|                                                                |
|----[ M0.0 ]---------------------------------------------------( Q50.5 )----|
```
Explanation:
- If Auto mode is selected (I50.0), set AutoMode (M0.0).
- If AutoMode (M0.0) is active, turn on the System Running Lamp (Q50.5).

##### 2. Sequence Control Logic

**Sequence Initialization:**

```plaintext
|----[ M0.0 ]----[ I41.3 ]----------------------------------( R MW100 )----|
```
Explanation:
- If Auto mode is active (M0.0) and Start button (I41.3) is pressed, reset Sequence Step (MW100) to 0.

**Step 0: Move to Home Position**

```plaintext
|----[ MW100 == 0 ]----[ I50.0 ]----[ I41.3 ]----------------------------( MW100 = 1 )----|

|----[ MW100 == 1 ]----[ NOT I40.5 ]--------------------( Q50.2 )----|
|                                      |
|----[ I40.5 ]-----------------------------( MW100 = 2 )----|
```
Explanation:
- If in Step 0 (MW100 == 0) and Auto mode (I50.0) and Start button (I41.3) are pressed, move to Step 1.
- In Step 1, if Positioner is not retracted (NOT I40.5), activate Retract Positioner (Q50.2).
- When Positioner is retracted (I40.5), move to Step 2.

**Step 2: Wait for Part Present**

```plaintext
|----[ MW100 == 2 ]----[ I40.0 ]-----------------------------( MW100 = 3 )----|
```
Explanation:
- If in Step 2 (MW100 == 2) and Part is present (I40.0), move to Step 3.

**Step 3: Extend Positioner**

```plaintext
|----[ MW100 == 3 ]-----------------------------( Q50.3 )----|
|                                      |
|----[ I40.6 ]-----------------------------( MW100 = 4 )----|
```
Explanation:
- If in Step 3 (MW100 == 3), activate Extend Positioner (Q50.3).
- When Positioner is extended (I40.6), move to Step 4.

**Step 4: Extend Part Pickup and Clamp Part**

```plaintext
|----[ MW100 == 4 ]-----------------------------( Q50.0 )----|
|                                      |
|----[ I40.2 ]-----------------------------( Q50.1 )----|
|                                      |
|----[ I40.4 ]-----------------------------( MW100 = 5 )----|
```
Explanation:
- If in Step 4 (MW100 == 4), activate Extend Part Pickup (Q50.0).
- When Part Pickup is extended (I40.2), activate Clamp (Q50.1).
- When Clamp is activated (I40.4), move to Step 5.

**Step 5: Retract Part Pickup and Positioner**

```plaintext
|----[ MW100 == 5 ]-----------------------------( NOT Q50.0 )----|
|                                      |
|----[ I40.1 ]-----------------------------( NOT Q50.3 )----|
|                                      |
|----[ I40.5 ]-----------------------------( MW100 = 6 )----|
```
Explanation:
- If in Step 5 (MW100 == 5), deactivate Extend Part Pickup (NOT Q50.0).
- When Part Pickup is retracted (I40.1), deactivate Extend Positioner (NOT Q50.3).
- When Positioner is retracted (I40.5), move to Step 6.

**Step 6: Indicate Part in Home Position**

```plaintext
|----[ MW100 == 6 ]-----------------------------( M0.1 )----|
|                                      |
|----[ I41.4 ]-----------------------------( NOT M0.1 )----|
|                                      |
|----[ NOT I50.0 ]-----------------------------( MW100 = 0 )----|
```
Explanation:
- If in Step 6 (MW100 == 6), set PartInHomePos (M0.1).
- If Index button (I41.4) is pressed, reset PartInHomePos (NOT M0.1).
- If Auto mode is deactivated (NOT I50.0), reset sequence to Step 0 (MW100 = 0).

##### 3. Safety and Reset Logic

**Emergency Stop and Stop Button:**

```plaintext
|----[ I41.6 ]----[ I41.5 ]-----------------------------( MW100 = 0 )----|
|                                      |
|----[ MW100 == 0 ]-------------------------------------( R Q50.0 )----|
|----[ MW100 == 0 ]-------------------------------------( R Q50.1 )----|
|----[ MW100 == 0 ]-------------------------------------( R Q50.2 )----|
|----[ MW100 == 0 ]-------------------------------------( R Q50.3 )----|
```

Explanation:
- If Emergency Stop (I41.6) or Stop button (I41.5) is pressed, reset sequence to Step 0 (MW100 = 0) and deactivate all outputs.

**Pressure Switch:**

```plaintext
|----[ NOT I40.7 ]--------------------------------------( MW100 = 0 )----|
```
Explanation:
- If Pressure Switch (I40.7) is not active, reset sequence to Step 0 (MW100 = 0).

**Reset Button:**

```plaintext
|----[ I41.2 ]-----------------------------( MW100 = 0 )----|
```
Explanation:
- If Reset button (I41.2) is pressed, reset sequence to Step 0 (MW100 = 0).

This structured Ladder Logic program ensures the safe and correct operation of the described process, fulfilling all the specified requirements and conditions.

## Question 4 (Total Marks: 25)

A client currently has a hydroelectric generation facility which uses water from the upper lake to generate power to support peak production demands, as illustrated in Figure 3. The client wants to update their current control system to ensure they can expand their current PLC control and SCADA monitoring capabilities, and allow for future expansion.  

![Figure 3](images/exam-2019-advanced-plcs-hmi-and-scada-autm07018/figure-3.jpeg)

> Figure 3

The client has requested detailed information in the sections of question 5 below, with regard to investing in a Fieldbus network to connect the I/O and control devices to the PLC/SCADA system.

### Question 4(a) [7 Marks]

The distance from the furthest control item at the upper lake to the control room is approximately 600 metres. It has been estimated from the current system that approximately 50 fieldbus nodes would be required to connect the existing I/O and control devices in the system. However, future expansion of the control system is anticipated so the client has suggested that at least 50% future expansion capability should be provided on the fieldbus network, in order to accommodate future fieldbus nodes being added to the control system.

1. Suggest a suitable Fieldbus type that would meet the client’s needs. Support your answer with a detailed explanation of how the fieldbus system will function and why this fieldbus type would be suitable for the requested system.

#### Question 4(a) Answer

**Suggested Fieldbus Type: PROFIBUS-DP**

##### Explanation of Functionality:

PROFIBUS-DP (Decentralized Periphery) is a widely used fieldbus system designed for high-speed communication between automation systems and decentralized I/O. It operates on a master-slave architecture, where the master controls the communication on the bus and the slaves respond to the master's requests.

**How the System Functions:**
- **Master-Slave Communication:** The PROFIBUS-DP master initiates communication with the slaves. Each slave has a unique address, and the master sends data to and requests data from the slaves in a cyclic manner.
- **Cyclic Data Exchange:** The master sends output data to the slaves and receives input data in return. This exchange happens in predefined cycles, ensuring real-time communication.
- **Data Transmission Speed:** PROFIBUS-DP can achieve data transmission speeds up to 12 Mbps, suitable for real-time control applications.
- **Network Topology:** The network can be configured in a line, tree, or star topology, providing flexibility in physical layout.

**Suitability for the Requested System:**
- **Distance and Nodes:** PROFIBUS-DP supports cable lengths up to 1200 meters at lower speeds, which fits the 600-meter requirement. It can handle up to 126 nodes on a single network, supporting current and future expansion needs (up to 75 nodes as per 50% future expansion requirement).
- **Robustness:** It is designed for industrial environments, offering high reliability and noise immunity, which is critical for a hydroelectric system.
- **Scalability:** The ability to add additional nodes easily makes it suitable for systems anticipating future expansion.
- **Interoperability:** PROFIBUS-DP is widely supported by many device manufacturers, ensuring compatibility and integration ease.


The client should consider using the **PROFIBUS** fieldbus system. PROFIBUS is a fieldbus network that is widely used in industrial automation systems. It is a digital communication system that allows for the communication of field devices with the control system. PROFIBUS is suitable for the client's system because it is a robust and reliable fieldbus system that can handle the long distances between the control items at the upper lake and the control room. It is also capable of handling a large number of field devices, which makes it suitable for the client's system.

### Question 4(b) (4 Marks)

Give possible advantages and disadvantages of using fieldbus in this hydroelectric system and support your answer with a brief explanation for each suggestion.

#### Question 4(b) Answer


**Advantages of Using Fieldbus:**

1. **Reduced Wiring:**
   - **Explanation:** Fieldbus networks reduce the need for extensive point-to-point wiring, consolidating multiple signals onto a single cable.
   - **Benefit:** This simplifies installation, reduces costs, and minimizes the potential for wiring errors.

2. **Enhanced Diagnostics:**
   - **Explanation:** Fieldbus systems provide detailed diagnostic information about network and device status.
   - **Benefit:** This allows for proactive maintenance and quicker troubleshooting, improving system reliability and reducing downtime.

3. **Flexibility and Scalability:**
   - **Explanation:** Fieldbus networks make it easy to add or reconfigure devices.
   - **Benefit:** This flexibility supports future system expansions and modifications without significant rewiring.

4. **Improved Data Integrity:**
   - **Explanation:** Digital communication on fieldbus networks is less susceptible to noise and signal degradation compared to analog signals.
   - **Benefit:** Ensures accurate and reliable data transmission, critical for control system performance.

**Disadvantages of Using Fieldbus:**

1. **Initial Setup Complexity:**
   - **Explanation:** Setting up a fieldbus network requires proper configuration of addresses, communication parameters, and device profiles.
   - **Drawback:** This complexity can increase the time and expertise needed for initial installation and commissioning.

2. **Higher Initial Cost:**
   - **Explanation:** Fieldbus-compatible devices and network components can be more expensive than traditional analog devices.
   - **Drawback:** The initial investment can be higher, although this may be offset by long-term savings in wiring and maintenance.

3. **Dependence on Network Health:**
   - **Explanation:** The entire communication relies on the health of the network. Any issues can disrupt communication to multiple devices.
   - **Drawback:** Network issues can have widespread impacts, potentially affecting the entire control system.

4. **Learning Curve:**
   - **Explanation:** Fieldbus systems require specific knowledge for setup and troubleshooting.
   - **Drawback:** Operators and maintenance personnel may need additional training to manage and maintain the system effectively.

### Question 4(c) [4 Marks]

Describe and illustrate the chosen fieldbus cable in detail. Show the location of the terminating resistors in the system.

#### Question 4(c) Answer


**Fieldbus Cable Description:**

- **Cable Type:** Shielded twisted pair cable, specifically designed for PROFIBUS-DP.
- **Conductors:** Typically 2 or 4 conductors.
- **Impedance:** 150 ohms.
- **Shielding:** Overall braided shield to protect against electromagnetic interference (EMI).
- **Color Coding:** Standardized color coding for easy identification (e.g., green and red for PROFIBUS-DP).

**Terminating Resistors:**

- **Location:** Terminating resistors are placed at both ends of the PROFIBUS-DP segment.
- **Value:** Typically, 220 ohms resistors are used to match the cable impedance.
- **Purpose:** Terminating resistors prevent signal reflections that can cause communication errors.

#### Illustration of Fieldbus Cable and Terminating Resistors:

```plaintext
 Control Room                            Upper Lake
+---------------------------------------------+
|                                             |
| PROFIBUS Master                            |
|                                             |
+-----+---------------------------------------+
      |                                       |
      |                                       |
      |   -----------------------------       |
      |   |                           |       |
      |   | Terminating Resistor (220Ω)|       |
      |   +-----------------------------       |
      |                                       |
      |------ PROFIBUS-DP Cable (600m) -------|
      |                                       |
      |                                       |
      |   -----------------------------       |
      |   |                           |       |
      |   | Terminating Resistor (220Ω)|       |
      |   +-----------------------------       |
      |                                       |
      +---------------------------------------+
      |                                       |
+-----+                                       |
| PROFIBUS Slaves                            |
|                                             |
+---------------------------------------------+
```

### Question 4(d) [6 Marks]

Due to the early stages of design for the new control system, it is undecided whether
a single or multi master station will be used in the Fieldbus network. Explain using
diagrams how cyclic communication would be initiated and controlled in:

1. Single Master system communicating with a number of slave devices
2. Multi Master System communicating with a number of slave devices

#### Question 4(d) Answer


##### 1. Single Master System Communicating with Slaves

**Diagram:**

```plaintext
   +-----------+       +---------+     +---------+
   | PROFIBUS  |       | Slave 1 |     | Slave 2 |
   | Master    |-------|         |-----|         |
   |           |       +---------+     +---------+
   +-----------+              |              |
                              |              |
                              +---------+    +---------+
                                        |    | Slave N  |
                                        +----|         |
                                             +---------+
```

**Explanation:**
- The single master controls all communication on the bus.
- The master polls each slave cyclically, sending output data and requesting input data.
- Each slave responds with its data during its assigned time slot.
- The master ensures that only one device communicates at a time to avoid collisions.

##### 2. Multi Master System Communicating with Slaves

**Diagram:**

```plaintext
   +-----------+       +---------+     +---------+
   | PROFIBUS  |       | Slave 1 |     | Slave 2 |
   | Master 1  |-------|         |-----|         |
   |           |       +---------+     +---------+
   +-----------+              |              |
                              |              |
                              +---------+    +---------+
                                        |    | Slave N  |
                                        +----|         |
                                             +---------+
   +-----------+       +---------+     +---------+
   | PROFIBUS  |       | Slave 1 |     | Slave 2 |
   | Master 2  |-------|         |-----|         |
   |           |       +---------+     +---------+
   +-----------+              |              |
                              |              |
                              +---------+    +---------+
                                        |    | Slave N  |
                                        +----|         |
                                             +---------+
```

**Explanation:**
- Multiple masters share the same bus, each controlling its own set of slaves.
- Masters coordinate access to the bus using a token-passing mechanism to prevent collisions.
- Each master has a predefined time slot to communicate with its slaves.
- When a master holds the token, it can communicate with its slaves, then passes the token to the next master.

### Question 4(e) [4 Marks]

One of the control devices to be used in the system is a turbine control valve. This control device will be required to be a slave on the fieldbus network. Explain the function of the required data file used to incorporate such a device on a fieldbus network.

#### Question 4(e) Answer

**Function of the Required Data File:**

The required data file for incorporating a turbine control valve (or any fieldbus device) on a fieldbus network is the **GSD file (General Station Description)**.

**Explanation:**

- **Device Description:** The GSD file provides a detailed description of the device, including its communication parameters, supported functions, and data structure.
- **Configuration:** It is used by the fieldbus master (or configuration tool) to configure the network and integrate the device.
- **Communication Settings:** Specifies baud rate, addresses, timing, and other critical communication parameters.
- **Modularity:** Defines the modular structure of the device, such as the number of I/O points, data formats, and specific functions supported.
- **Interoperability:** Ensures that devices from different manufacturers can be integrated into the same network, provided they adhere to the fieldbus standard.

By using the GSD file, the master can correctly communicate with the turbine control valve, ensuring it receives the appropriate commands and sends the required status information.

## Question 5 (Total Marks: 25)

### Question 5(a) [4 Marks]

Explain the function of a P&ID diagram and describe using an example the function of device tag descriptors and numbering.

#### Question 5(a) Answer

**Function of a P&ID Diagram:**

A Piping and Instrumentation Diagram (P&ID) is a detailed graphical representation of a process system's piping, instrumentation, and control devices. It serves several critical functions:

- **Design and Engineering:** Provides a clear layout for the design and engineering of a process plant.
- **Operation:** Assists operators in understanding the process flow and the functioning of the system.
- **Maintenance:** Helps maintenance personnel locate and identify system components for troubleshooting and repair.
- **Safety and Compliance:** Ensures that all safety and regulatory requirements are met by illustrating safety devices and control systems.

**Example of Device Tag Descriptors and Numbering:**

Device tag descriptors and numbering on a P&ID provide unique identifiers and descriptive information for each instrument and control device. 

- **Tag Descriptor:** Typically a combination of letters and numbers that describe the type of instrument and its function. For example, "FT" could represent a flow transmitter.
- **Numbering:** A unique identifier following the descriptor, often indicating the specific loop or sequence in the system. For example, "FT-101" would be a flow transmitter in loop 101.

Example:
- **Tag: FT-101**
  - **FT:** Flow Transmitter
  - **101:** Loop number 101

This tag helps engineers and technicians quickly identify the instrument, understand its function, and locate it within the system.

### Question 5(b) [3 Marks]

Instrument location can be shown on a P&ID diagram using the presence, absence or type of a line within the circle, as illustrated in Figure 4.

```mermaid
graph TD
    A(("&nbsp;&nbsp;&nbsp;&nbsp;FIT&nbsp;&nbsp;&nbsp;&nbsp;<br/>&nbsp;<br/>123"))
    B(("&nbsp;&nbsp;&nbsp;&nbsp;TIT&nbsp;&nbsp;&nbsp;&nbsp;<br/>_______<br/>123"))
    C(("&nbsp;&nbsp;&nbsp;&nbsp;FCV&nbsp;&nbsp;&nbsp;&nbsp;<br/>-------<br/>123"))
```

![Figure 4](images/exam-2019-advanced-plcs-hmi-and-scada-autm07018/figure-4.png)

> Figure 4

1. List the instrument location when no line is present#
2. List the instrument location when a solid line is present
3. List the instrument location when a broken line is present.

#### Question 5(b) Answer


**Instrument Location on a P&ID Diagram:**

1. **No Line Present:**
   - **Location:** Field-mounted instrument
   - **Explanation:** Instruments with no line within the circle are typically located in the field, meaning they are installed directly on the process equipment.

2. **Solid Line Present:**
   - **Location:** Control room-mounted instrument
   - **Explanation:** Instruments with a solid line within the circle are located in the control room, indicating they are part of a centralized control system.

3. **Broken Line Present:**
   - **Location:** Auxiliary or local panel
   - **Explanation:** Instruments with a broken line within the circle are located on an auxiliary or local panel, which could be a local control station or panel near the process equipment.

### Question 5(c) [8 Marks]

A client has sought expertise on investing in OPC connectivity. They have a number of data sink applications that require data from industrial source devices, and they request the following.

1. Explain to the client the benefits of investing in and using OPC connectivity
2. Explain the types of data that OPC supports

#### Question 5(c) Answer

**Benefits of Investing in and Using OPC Connectivity:**

1. **Interoperability:**
   - **Explanation:** OPC (OLE for Process Control) provides a standard interface for different hardware and software systems to communicate, regardless of the manufacturer. This ensures seamless data exchange between various devices and systems in an industrial environment.
   - **Benefit:** Reduces integration complexity and allows for a diverse range of devices to work together effectively.

2. **Scalability:**
   - **Explanation:** OPC allows for easy scaling of systems by adding new devices and applications without significant reconfiguration.
   - **Benefit:** Supports future expansion and upgrades, making the system adaptable to changing requirements.

3. **Real-Time Data Access:**
   - **Explanation:** OPC provides real-time access to process data, ensuring timely information for decision-making.
   - **Benefit:** Enhances operational efficiency and responsiveness by providing up-to-date information.

4. **Reduced Cost:**
   - **Explanation:** Standardizing communication protocols with OPC reduces the need for custom integration solutions.
   - **Benefit:** Lowers development and maintenance costs by using widely supported and understood standards.

### Question 5(d) [6 Marks]

Explain the functionality of an OPC server. Include a diagram to support your
explanation, illustrating the conceptual view of the inner workings of the OPC server.

#### Question 5(d) Answer


**Functionality of an OPC Server:**

An OPC server acts as an intermediary between various hardware devices and software applications. It collects data from the devices, processes it, and makes it available to client applications.

**Diagram:**

```plaintext
+------------------+       +---------------+       +-----------------+
|  Field Devices   |<----->|    OPC Server |<----->| Client Software |
| (Sensors, PLCs)  |       +---------------+       |  (SCADA, HMI)   |
|                  |       |               |       |                 |
+------------------+       | - Collects    |       | - Displays Data |
                           |   Data        |       | - Analyzes Data |
                           | - Processes   |       | - Issues Commands|
                           |   Data        |       |                 |
                           | - Manages     |       +-----------------+
                           |   Communication|
                           +---------------+
```

**Explanation:**

- **Data Collection:** The OPC server communicates with field devices using various protocols (e.g., Modbus, PROFIBUS) to collect data.
- **Data Processing:** It processes the collected data, ensuring it is in a standardized format.
- **Data Availability:** The processed data is made available to client software applications (e.g., SCADA, HMI) through the OPC interface.
- **Communication Management:** The OPC server manages communication between multiple devices and client applications, ensuring data integrity and timely updates.

### Question 5(e) (4 Marks)

Explain the types of data sources that OPC servers communicate with.

#### Question 5(e) Answer


**Types of Data Sources OPC Servers Communicate With:**

1. **PLC (Programmable Logic Controllers):**
   - **Function:** Controls machinery and processes in industrial environments.
   - **Communication:** OPC servers read and write data to PLCs to monitor and control operations.

2. **DCS (Distributed Control Systems):**
   - **Function:** Manages complex processes across large-scale industrial operations.
   - **Communication:** OPC servers integrate with DCS to provide a unified control and monitoring system.

3. **SCADA Systems (Supervisory Control and Data Acquisition):**
   - **Function:** Supervises and controls industrial processes.
   - **Communication:** OPC servers facilitate data exchange between SCADA systems and field devices for real-time monitoring and control.

4. **Sensors and Actuators:**
   - **Function:** Collect process data and execute control commands.
   - **Communication:** OPC servers gather data from sensors (e.g., temperature, pressure) and send control commands to actuators (e.g., valves, motors).

5. **HMI (Human-Machine Interface) Panels:**
   - **Function:** Provide user interfaces for operators to monitor and control processes.
   - **Communication:** OPC servers supply data to HMI panels, enabling real-time display and interaction.

By facilitating communication between these data sources and client applications, OPC servers ensure efficient and reliable process control and monitoring.


```mermaid
graph LR
    A["Field Devices <br>(Sensors, PLCs)"] <---> B["OPC Server <br> - Collects Data<br> - Processes Data<br> - Manages Communication"]
    B <---> C["Client Software <br> (SCADA, HMI) <br> - Displays Data<br> - Analyzes Data<br> - Issues Commands"]
```

```mermaid
classDiagram
    class FieldDevices["Field Devices"] {
        Sensors
        PLCs
    }
    class OPCServer["OPC Server"] {
        Collects Data
        Processes Data
        Manages Communication
    }
    class ClientSoftware["Client Software"] {
        Displays Data
        Analyzes Data
        Issues Commands
    }

    FieldDevices <--> OPCServer
    OPCServer <--> ClientSoftware
```
  
```plantuml
@startuml

skinparam rectangle {
    BackgroundColor LightSkyBlue
    BorderColor Black
}

rectangle "Field Devices \n(Sensors, PLCs)" as A
rectangle "OPC Server \n - Collects Data\n - Processes Data\n - Manages Communication" as B
rectangle "Client Software \n(SCADA, HMI) \n - Displays Data\n - Analyzes Data\n - Issues Commands" as C

A <---> B
B <---> C
@enduml
```
