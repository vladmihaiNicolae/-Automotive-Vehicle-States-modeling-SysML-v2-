# -Automotive-Systems-Engineering : Vehicle-States-modeling-SysML-v2-
A conceptual Model-Based Systems Engineering (MBSE) project demonstrating the power-state transitions and requirements of a modern automotive ECU using the new SysML v2 standard

*Note: This is a personal research project. All architectures, requirements, and behaviors modeled here are generic and do not contain any proprietary or confidential data.*

The goal of this personal project is to explore the capabilities of the text-based systems modeling notation (KerML/SysML v2) and apply it to a modern automotive subsystem.

### Modeled system : power supply
The project focuses on modeling the functional and structural aspects of an automotive accessory power supply sub-system

### System architecture and concepts applied
- a state diagram for accessories sub-states
- the architecture of elements contributing to accessories sub-states state machine (eg RF key module, key cylinder sensor, CAN bus, door sensor)
- requirements and use-cases for passing between different states
- action flow diagram, from vehicle sleeping / locked to engine running (including if condition)

### Tools used
Jupyter Lab for both code and diagram generation
