# Programmable Structures

---

## What is an FPGA?

**FPGA (Field Programmable Gate Array)** is a type of integrated circuit that can be reprogrammed by the user for various tasks. This flexibility allows designers to change and reload their hardware designs.

### Advantages of FPGAs

* **Reconfigurability:** Designs can be easily modified and re-uploaded, providing great flexibility for designers.
* **Speed and Parallel Processing:** FPGAs can perform multiple tasks simultaneously, making them ideal for high-speed applications like image processing.

## Hardware Description Language (HDL)

**Hardware Description Languages (HDL)** are a class of computer languages used to define and describe electronic circuits. They allow designers to simulate and verify a circuit's functionality.

* HDL is used to program FPGAs. The most common HDLs are **VHDL** and **Verilog**.

### Verilog Module

A Verilog module is a block of code that implements a specific function. A complex system can be built from multiple modules. There are three types of modeling in Verilog:
* **Structural:** Describes the design in terms of components and their interconnections.
* **Dataflow:** Describes the flow of data through the design.
* **Behavioral:** Describes the behavior of the design at a higher level of abstraction.

---

## Logic Circuits

### Combinational Logic Circuits
These are digital circuits without a memory element. The output of the circuit depends solely on its current inputs.

There are three main ways to describe a combinational logic circuit:
1.  **Boolean Algebra:** An algebraic expression representing the circuit's function.
2.  **Truth Table:** A table that lists all possible input combinations and their corresponding outputs.
3.  **Logic Diagram:** A graphical representation of the circuit using standard logic gate symbols.

### Sequential Logic Circuits
These circuits contain memory elements. Their output depends on the **current input**, **past input**, and **past output**. They can "remember" past states until a clock signal triggers a change.

Sequential circuits are categorized as:
1.  **Event-Driven (Asynchronous):** They react immediately to an event at the input.
2.  **Clock-Driven (Synchronous):** State changes are synchronized with a clock signal.
3.  **Pulse-Oriented (Hybrid):** They respond to both clock signals and trigger pulses.

### Blocking vs. Non-Blocking Assignments

These are specific to HDLs.
* **Blocking Assignments (`=`):** Used for combinational logic. They are executed sequentially; a statement cannot start until the previous one is complete.
* **Non-Blocking Assignments (`<=`):** Used for sequential logic. They are evaluated in parallel, and the assignments take effect at the end of the current time step (e.g., on a clock edge).

---

## Finite State Machines (FSMs)

An **FSM** models the behavior of a system based on states and the transitions between them.

FSMs are visualized using two main types of diagrams:
1.  **State Transition Diagram:**
    * **States:** Represented by nodes (circles) showing the different states of the system.
    * **Transitions:** Represented by arrows, indicating a move from one state to another.
    * **Events:** Conditions or events that trigger a state transition.
2.  **Algorithmic State Machine (ASM) Diagram:**
    * **Start/End Points:** Mark the beginning and end of the algorithm.
    * **Actions:** Rectangles representing actions the algorithm performs.
    * **Decision Points:** Diamond shapes representing conditions that lead to different paths.
    * **Flow Lines:** Arrows indicating the flow of the algorithm.