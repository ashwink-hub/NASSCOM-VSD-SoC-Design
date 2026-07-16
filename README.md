
# NASSCOM-VSD-SoC-Design
Digital VLSI SoC design and planning workshop with complete RTL2GDSII flow organised by VSD in collaboration with NASSCOM (Advanced Physical Design using OpenLANE/Sky130)
# Sky130 Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK

## SKY130_D1_SK1 - How to talk to computers

### SKY_L1 - Introduction to QFN-48 Package, chip, pads, core, die and IPs

<img width="887" height="852" alt="image" src="https://github.com/user-attachments/assets/8dd4444c-64b2-42ad-ad74-2e116b80ffbd" />

#### Package

What we call "the chip" on a board is actually just the **package** a protective cover around the real chip. The real chip sits inside, tiny and fragile, connected to the package pins by thin wires (**wire bonding**).

#### Chip
<img width="1296" height="857" alt="image" src="https://github.com/user-attachments/assets/c8219650-b99e-4de5-a74b-c056a7502146" />

<img width="1248" height="855" alt="image" src="https://github.com/user-attachments/assets/c5743e31-123d-424a-8fdc-893c3b2f5c61" />


Inside the real chip:

- **Pads** — where signals enter and exit the chip.
- **Core** — the area inside the pads, holding all the digital logic.
- **Die** — pads + core together. This is the basic unit of a manufactured chip.

### Foundry

A **foundry** is the factory where chips are manufactured.
<img width="1067" height="596" alt="image" src="https://github.com/user-attachments/assets/b1463dd7-1861-4000-8a86-22f33d4e1ae6" />

- **Foundry IP** — specialized blocks tied to a specific foundry, needing expert design.
- **Macros** — reusable, repeatable digital logic blocks.

  
### SKY_L2 - Introduction to RISC-V

#### From C Program to Chip

<img width="1245" height="796" alt="image" src="https://github.com/user-attachments/assets/1fc15c14-c856-481d-9191-5f8b4cd9f572" />


A C program has to eventually run on real hardware — the chip inside your laptop. Getting there follows a set flow.

1. **Compile to Assembly** — The C program is compiled into an assembly language program, based on the **RISC-V ISA** (Reduced Instruction Set Computing - V Instruction Set Architecture).
2. **Assemble to Machine Code** — The assembly program is converted into machine language — plain binary (0s and 1s) that the hardware can understand.
3. **Implement in RTL** — The RISC-V specification is implemented using RTL (a Hardware Description Language).
4. **RTL to Layout** — The RTL is taken through the standard **RTL to GDSII** flow (PnR) to produce the final chip layout.

## SKY130_D1_SK2 - SoC design and OpenLANE

### SKY_L1 - Introduction to all components of open-source digital asic design

For the digital ASIC Design, there are three important things required
1. RTL IP's
2. EDA Tools
3. PDK Data

<img width="1281" height="721" alt="image" src="https://github.com/user-attachments/assets/2a4e5348-68b3-42f7-8d64-bccd81f89c35" />

What is mean by PDK ?
      The PDK also called as the process development kit, that contains the collection of files used to model a fabrication process for the EDA tools to design an IC (Integrated Chip). It act as an interface between the FAB and the designers. 
      SKY130nm is a open-source pdk, available at github.com/google/skywater-pdk
### SKY_L2 - Simplified RTL2GDS flow :

<img width="781" height="416" alt="image" src="https://github.com/user-attachments/assets/77f34c2f-71ff-46a0-aa58-e9399a463485" />


The above image is the simplified RTL Design flow
The major step is the synthesis
It converts the RTL code into a standard cell library

<img width="1121" height="617" alt="image" src="https://github.com/user-attachments/assets/93e342e4-80fb-4056-a5b1-0c25879f6494" />


In the floor planning,

<img width="1125" height="617" alt="image" src="https://github.com/user-attachments/assets/31dab87e-9e35-41c1-b997-16aa67d3c00a" />


In chip floor planning the chip die is partitoned between different components

<img width="1118" height="627" alt="image" src="https://github.com/user-attachments/assets/52a55484-bbf6-4789-b49e-1e990066a91c" />


In this step, macro rows and routing steps were defined, which will be used later during pnr

<img width="1117" height="616" alt="image" src="https://github.com/user-attachments/assets/12baa072-4a75-4e96-bb87-216e4cdde3b0" />


In power planning, The power network is constructed, typically the chip is powered by vdd and
gnd pins
The power pins are the connected to all components, such parallel instructions are meant to
reduce the resistance
And to address the electro migration problem

<img width="1122" height="626" alt="image" src="https://github.com/user-attachments/assets/ee56bb55-7227-49dc-9850-840655f9faf4" />


Typically cell placement is done using two steps :
Global and Detailed Placement
Global placement finds the optimum position for all cells, it may not be legal, so cells may
overlap
In details placement, the positions obtained from the global placement is altered to be legal

<img width="1116" height="622" alt="image" src="https://github.com/user-attachments/assets/89e43ec7-8936-470e-b0eb-81dbf96d946f" />


After placement, comes routing, before routing we should create the clock distribution network

<img width="1120" height="622" alt="image" src="https://github.com/user-attachments/assets/5dfa6ad2-a6f7-448e-b550-f330ba52a5d0" />


After this, comes the signal routing using horizontal and vertical nets
THE SKY130 PDK CONTAINS THE SIX ROUTING LAYERS

<img width="1117" height="616" alt="image" src="https://github.com/user-attachments/assets/28af4469-87d4-4588-ab98-eb0727cab702" />


mostly routing grids are used as global and detailed routing,
Once routing is finished, we construct the final layout

<img width="1122" height="610" alt="image" src="https://github.com/user-attachments/assets/d06186e5-7c66-4b93-9211-f22afe7c5278" />


The final layout should undergo the above verification process
Atlast, timing analysis is done to check the layout running according to the specific timing

### SKY_L3 - Introduction to OpenLANE
and strive chipsets

<img width="1122" height="622" alt="image" src="https://github.com/user-attachments/assets/4dea9a4c-8dff-4c2a-a5a7-6a6e07ab39cf" />


It is opensource and free

<img width="1121" height="617" alt="image" src="https://github.com/user-attachments/assets/43f88297-51d8-4ac7-95ac-a861430a94eb" />

The below is the strive Soc family

<img width="1121" height="631" alt="image" src="https://github.com/user-attachments/assets/0baf3873-7180-4dab-8909-128c95fb4762" />


<img width="1123" height="512" alt="image" src="https://github.com/user-attachments/assets/5bb293ff-fb10-4bbe-a0ed-f28293c369c8" />


OpenLane can be used to generate macros and chips like the final layout
It has the two modes of operation :
Autonomous and Interative

<img width="1123" height="623" alt="image" src="https://github.com/user-attachments/assets/b51b1164-764a-47c3-97b3-293e78a84602" />


It comes with 43 best design examples and so on

### SKY_L4 - Introduction to OpenLane
detailed ASIC design flow

The below diagram shows the openLane flow

<img width="1120" height="625" alt="image" src="https://github.com/user-attachments/assets/00d89511-5cb6-46ed-802a-dacfb62f2cb7" />


OpenLane is based on several opensource projects

<img width="1122" height="628" alt="image" src="https://github.com/user-attachments/assets/254df92a-4d1c-4f18-9346-5253d221bcf5" />


It has the several process for the testing the design ,

<img width="1126" height="632" alt="image" src="https://github.com/user-attachments/assets/c48dc075-7d3d-4fe1-a699-2422136931b3" />


After testing comes the physical Implementation, which is completely run by OpenRoad

<img width="1126" height="625" alt="image" src="https://github.com/user-attachments/assets/2b56409d-c16c-4ccd-b02f-4a40b3b67c2f" />


The above process are done in the openRoad
The input to this process is the gate level netlist which is prepared after the synthesis

<img width="1120" height="612" alt="image" src="https://github.com/user-attachments/assets/12ff8118-fa22-4a20-a3c1-430a70868f12" />


After the netlist is prepared the logic verification test should be carried out
The main reason for the LEC test is to confirm that the function did not change after modifying
the netlist

Dealing with the Antenna Rule Violation

<img width="1117" height="623" alt="image" src="https://github.com/user-attachments/assets/0eb7e81c-bd01-4f28-a9fe-1d8860350100" />


It damages the transistor gates during fabrication
There is two solution with deal with this problem
1. Bridging

<img width="1122" height="623" alt="image" src="https://github.com/user-attachments/assets/9090f68a-e0f5-4b2f-ae01-fc7cb76d7571" />


2. Adding antena diode

<img width="1121" height="626" alt="image" src="https://github.com/user-attachments/assets/c0209817-0dbe-4ab4-b1a2-35e12eb963c0" />


In openLance, we take the preventive approach

<img width="1118" height="652" alt="image" src="https://github.com/user-attachments/assets/091b45db-31a9-443d-8455-ecc4b06aa171" />


The open sta from the openroad is used to check the timing violation(Static Timing Analysis)
And the physical verification of DRC and LVS is checked using the Magic Tool

<img width="1122" height="638" alt="image" src="https://github.com/user-attachments/assets/0381e3f0-4825-4618-a7ca-ea3ece42e139" />

# SKY130_D1_SK3 - Getting Familiar with Open-Source EDA Tools

## SKY_L1 - OpenLANE Directory Structure in Detail

This module covers the OpenLANE tool itself — its directory structure, commands, and environment — along with how to invoke and run it.

### Useful Linux Commands

| Command | Description |
|---|---|
| `ls` | List files in a directory |
| `ls -ltr` | List files in chronological order (oldest to newest) |
| `cd` | Change directory |
| `less` | Open and view a file |
| `clear` | Clear the terminal screen |

To learn more about any command, you can run:

```bash
command_name --help
```

### Navigating to the OpenLANE Directory

```bash
cd /Desktop/work/tools/openlane_working_dir
```

### OpenLANE Directory Overview

- **`libs.ref`** — Contains files specific to the PDK (Process Design Kit).
- **`libs.tech`** — Contains files specific to individual tools/technologies, such as ngspice, OpenLANE, and Magic.

### PDK (Process Development Kit)

This folder holds all the information related to the PDK. We're using the **SKY130nm PDK**, which is open-source. OpenLANE itself is built around this PDK — it's the foundation the entire flow relies on.

---

## SKY_L2 - Design Preparation Step

OpenLANE should be run in **interactive mode**; otherwise, it processes everything automatically without letting you inspect each stage.

### Steps

1. **Import the required packages** to load OpenLANE's commands.
2. All designs live in the `designs` folder inside OpenLANE.
   - The **`src`** folder contains the source files — Verilog and SDC (timing constraints) information.
   - **`config.tcl`** overrides any default configuration — anything set here takes priority over OpenLANE's defaults.
   - The **`sky130A.xx`** file holds default values provided by OpenLANE. Removing it won't break the flow since these are just fallback defaults.
3. Before running synthesis, the file system needs to be set up — this is the **design setup stage**.

### Command to Prep the Design

```bash
prep -design picorv32a
```

---

## SKY_L3 - Reviewing Files After Design Prep and Running Synthesis

Before running synthesis, the `prep` step creates a new set of files and folders for our design.

### Inside the `runs` Folder

A new run folder is created, named with **today's date**.

- **`tmp`** — Empty at this stage; used for temporary files during the run.
- **`results`** — Will hold the results of synthesis and later stages.
- **`reports`** — Contains reports generated at every step of the flow.
- **`config.tcl`** — Stores the default parameters used for this run.
- **`commands`** file — Logs the commands that were used during the run.

A merged LEF file is also created at this stage.

### Run Synthesis

```bash
run_synthesis
```

---

## SKY_L4 - OpenLANE Project Git Link & Description

### Recommended YouTube Videos

- **FOSSi Dial-up** — "An Intro to OpenLANE and the SkyWater PDK"

### GitHub Repository

- [`efabless/openlane`](https://github.com/efabless/openlane) — Contains all the official information, documentation, and source code for OpenLANE.

---

## SKY_L5 - Steps to Characterize Synthesis Results

The first objective after synthesis is to calculate the **flop ratio** — the proportion of D flip-flops among all the cells used.

### Flop Ratio Formula

```
Flop Ratio = (Total number of D Flip-Flop cells / Total number of cells) × 100
```

The relevant files for this calculation can be found in the **synthesis** and **reports** folders.

# Lab Implementation - Running the OpenLANE Flow (Interactive Mode)

This document walks through the basic commands used to invoke OpenLANE and run synthesis on a design (`picorv32a`) inside its Docker environment.

## Step 1: Navigate to the OpenLANE Directory

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-14-16" src="https://github.com/user-attachments/assets/4c064432-72bf-4264-b72d-c0631f8cc41b" />


Move into the folder where OpenLANE is installed and set up.

## Step 2: Enter the OpenLANE Docker Container

```bash
# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
docker
```

OpenLANE runs inside a Docker container so that all its tools and dependencies work the same way on any machine. To avoid typing that long `docker run` command every time, it's usually saved as an alias called `docker`. Once the alias is set, simply typing `docker` drops you into the OpenLANE container, with your current folder mounted inside it so files can be shared between your machine and the container.

<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-25-37" src="https://github.com/user-attachments/assets/d614fb9d-d803-450a-a555-247a8bc7dd34" />

## Step 3: Launch OpenLANE in Interactive Mode

```bash./flow.tcl -interactive
```

This starts the OpenLANE flow, but instead of running everything automatically end-to-end, it opens an interactive shell where you can run each stage of the flow step by step. This is helpful for learning the flow or debugging a specific stage.

<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-26-51" src="https://github.com/user-attachments/assets/0927e997-29b6-4f91-9c1e-27108417957a" />


## Step 4: Load the OpenLANE Package

```bash
package require openlane 0.9
```
<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-28-10" src="https://github.com/user-attachments/assets/908cc0f9-b2c6-47b7-8486-03f7cbb25e0f" />

This loads the OpenLANE Tcl package (version 0.9) so all the flow commands become available for use.

## Step 5: Prep the Design

```bash
prep -design picorv32a
```

Before running any stage of the flow, the design needs to be "prepped." This command sets up the required directories, merges the PDK and design-specific configuration files, and creates a fresh run folder to store all the outputs for this particular run. Here, we're prepping the `picorv32a` design.

<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-29-26" src="https://github.com/user-attachments/assets/a439a1f4-4ec3-4b87-a43a-2304b2a99452" />


## Step 6: Run Synthesis

```bash
run_synthesis
```

<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-31-42" src="https://github.com/user-attachments/assets/300ced02-a205-4f90-93aa-dbdfdbf4fe33" />


This runs the RTL synthesis stage, converting the design's RTL (written in Verilog) into a gate-level netlist made up of standard cells from the PDK library.

## Step 7: Exit OpenLANE

```bash
exit
```
<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-32-30" src="https://github.com/user-attachments/assets/134bea7f-ead0-4816-b66c-a5029f39b89d" />


Closes the interactive OpenLANE flow session.

## Step 8: Exit the Docker Container

```bash
exit
```
<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-32-58" src="https://github.com/user-attachments/assets/cdb767f5-284d-4ab4-af75-1df2882ca0a9" />


Closes the Docker container and returns you to your regular terminal.

## step 9: To find the flop ratio

Scroll up and find in the print statistics

<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-38-17" src="https://github.com/user-attachments/assets/1109eef5-6cc3-42ee-afbf-147b12f0260c" />

The Total number of the cell is 

<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-40-13" src="https://github.com/user-attachments/assets/b37707d0-d8b2-41a5-9f22-d6811bba418a" />

The final value of the flop ratio is 

<img width="1920" height="1080" alt="Screenshot from 2026-07-09 20-42-16" src="https://github.com/user-attachments/assets/114ce1df-393f-4d6d-8f9d-40d6b06ea015" />


# Sky130 Day 2 - Good floorplan vs bad floorplan and introduction to library cells

# SKY130_D2_SK1 - Chip Floor Planning Considerations

## SKY_L1 - Utilization Factor and Aspect Ratio

In the physical design overview, the first step is to define the **width** and **height** of the **Core** and **Die**.

A **netlist** defines the connectivity of all components in the design.

<img width="757" height="512" alt="image" src="https://github.com/user-attachments/assets/72230109-f6e1-4c29-8267-7398c3acda43" />


The image above shows the basic structure: the **Die** is the outer boundary, and the **Core** sits inside it — the core is where the horizontal rows (placement rows) for standard cells are laid out.

---

## Understanding the Netlist

Let's consider a simple example netlist:

- **FF** = Flip-Flops / Latches / Registers
- **A1, O1** = Standard Cells (AND gate, OR/Inverter gate)

The example netlist consists of **2 flip-flops and 2 gates**, connected as follows:

> **Note:** A "netlist" describes the connectivity of an electronic design.

<img width="830" height="615" alt="image" src="https://github.com/user-attachments/assets/e5879cf2-ee79-458f-bec1-c6a358f7d7a1" />

---

## Defining Core and Die Dimensions

While defining the dimensions of the chip, we are mostly defining the dimensions of the **logic gates** used. To find the dimensions of the core and die, we consider the **standard cells** that make up the logic gates.

By convention in this example:
- Each **standard cell** = 1 unit × 1 unit → **1 sq. unit** of area
- Each **flip-flop (FF)** = 1 unit × 1 unit → **1 sq. unit** of area

Roughly, the entire circuit (2 FFs + 2 standard cells) occupies **4 sq. units** of area.

<img width="617" height="515" alt="image" src="https://github.com/user-attachments/assets/bb989789-777a-40a6-b07f-c113668afee9" />


Inside the **Die**, the **Core** is placed. The **Core** is where we place the fundamental and actual logic of the design.

---

## What is "Core" and "Die"?

A **die** (which contains the core) is a small semiconductor material specimen on which the fundamental circuit is fabricated.



The **logical cells occupy the complete area of the core** in this idealized example, giving **100% utilization**.

<img width="1001" height="553" alt="image" src="https://github.com/user-attachments/assets/e8c33a08-cfa2-4535-9651-fe32b4601bbc" />


If there were some area left unused inside the core, utilization would be less than 100%. In this idealized example, no area is left out, so utilization is exactly 100%.

---

## Utilization Factor

The **Utilization Factor** is defined as:

```
                Area occupied by the logic cells (Netlist)
Utilization  =  --------------------------------------------
Factor                    Total area of the Core
```

<img width="700" height="503" alt="image" src="https://github.com/user-attachments/assets/42f49cbf-3295-44b6-b224-9d1a6c895dea" />




For the example above:

```
                (4 x 1 sq. unit)
Utilization  =  -----------------  =  1
Factor          (2 unit x 2 unit)
```

- When **Utilization Factor = 1**, the core is **completely optimized** (100% utilized).
- **Practically, designs do not target 100% utilization.** A typical target is around **60–80% utilization**, leaving room for routing, buffering, and optimization.

---

## Aspect Ratio

The **Aspect Ratio** is defined as:

```
Aspect Ratio = Height / Width
```

- If **Aspect Ratio = 1** → the chip is **square** shaped.
- If **Aspect Ratio ≠ 1** → the chip is **rectangular** shaped.

<img width="646" height="497" alt="image" src="https://github.com/user-attachments/assets/aa8e3945-71ac-4177-b638-0f7ae25d240e" />


---

## Example: Larger Die and Core Area

Now consider a bigger example where the **Die** is **4 units × 4 units**, but the actual logic (the same 2 FFs + A1 + O1 netlist) still only occupies a **2 unit × 2 unit** area.

<img width="982" height="552" alt="image" src="https://github.com/user-attachments/assets/d85f4581-8d83-46ff-b541-37fddcdecc95" />


Calculating the Utilization Factor for this case:

```
                (2 unit x 2 unit)
Utilization  =  -----------------  =  0.25
Factor          (4 unit x 4 unit)
```

<img width="938" height="552" alt="image" src="https://github.com/user-attachments/assets/47b9149d-976a-4435-ba4a-bec624279d83" />


**Interpretation:** Out of the complete chip area, only **25% is utilized**, and the remaining **75% is available** for placement optimization, buffering, routing resources, and other physical design needs.

<img width="932" height="551" alt="image" src="https://github.com/user-attachments/assets/46b58524-97e4-4c53-bc39-e31be90d9099" />

---
# Floorplanning Concepts: Pre-placed Cells, Power Planning & Pin Placement

## What Are Pre-placed Cells?

A combinational logic circuit performs a specific function, but as the design grows (say, to 50 gates), it becomes large and complex.

To manage this, we can split the circuit into smaller blocks — for example, two blocks of 25 gates each. Each block is then implemented independently, with its own extended I/O pins. When needed, these blocks are combined and connected together to perform the complete function.

Since these blocks are built only once but reused multiple times, they're often available as ready-made IPs in the market. Common examples include:

- Memory
- Clock-gating cells
- Comparators
- Multiplexers (Mux)

These reusable IP blocks are called **pre-placed cells**, and the process of arranging them on the chip is called **floorplanning**.

### Key Idea

- Pre-placed cells have **user-defined locations** and are placed on the chip *before* automated Placement-and-Routing (P&R) begins.
- The automated P&R tool then places all the remaining logical cells around them.
- These reusable blocks are also referred to as **macros** or **IPs**.

## Defining the Location of Pre-placed Cells

The placement location of these blocks is generally decided based on the **design summary** — most blocks communicate directly with input pins, so their location depends on the overall design scenario.

<!-- image -->

Once placed, these blocks are **fixed** — they cannot be moved further during the flow. To ensure stable operation, they are surrounded with **decoupling capacitors**.

## What Is a Decoupling Capacitor and Why Is It Needed?

Whenever a circuit switches from 0 to 1, it requires a sudden supply of current. 

A decoupling capacitor is essentially a large capacitor charged to the same voltage as the power supply. During a switching event, the circuit draws current from this capacitor instead of the main power supply — effectively **decoupling** the circuit from fluctuations in the input voltage.

- Every switching activity drains some charge from the decoupling capacitor.
- Once discharged, the capacitor recharges itself from the main power supply.

## How Does Global Communication Happen Through Power Planning?

Before discussing power planning, recall the current-demand problem addressed by decoupling capacitors. Now consider a macro that repeats multiple times across the chip — each instance independently demands current.

### The Voltage Drop Problem

Consider a signal sent from a driver to a load over a 16-bit bus:

- When the driver switches from logic 0 to logic 1, the line must retain enough power to remain stable.
- The power supply is the only real source for this — using a decoupling capacitor alone isn't practical here.
- If the macro is located far from the power supply, a **voltage drop** occurs along the way.

### The Simultaneous Switching Problem

Say this 16-bit bus feeds into an inverter. When the logic passes through:

- Bits going from 1 → 0 will discharge.
- Bits going from 0 → 1 will charge.

If this switching happens simultaneously across all bits, it creates a "bump" at the **ground tap point**. If this bump exceeds the noise margin, the circuit can enter an undefined state.

- **0 → 1 transition:** Demands additional current from the supply; a small voltage drop is acceptable as long as it stays within the noise margin.
- **1 → 0 transition:** Similarly affects the ground reference point.

### The Solution

The root problem is that power is supplied from a single point. If power is instead supplied from **multiple points** across the chip, this issue is significantly reduced — each block can draw current from its **nearest** power source rather than a single distant one.

## Pin Placement

General convention:

- **Input ports** → placed on the left side
- **Output ports** → placed on the right side

### Key Observations

1. The exact placement of input and output ports isn't fixed — it depends on how the internal blocks are arranged within the core.
2. **Clock ports** are made larger than other ports because the clock signal drives the entire chip. A larger port size means **lower resistance** along the path, ensuring the clock signal reaches everywhere reliably.

## Logical Cell Placement Blockage

To protect the pin locations, a **placement blockage** is defined — this prevents the automated Placement-and-Routing tool from placing any other cells too close to the pins.

Once this blockage is set, the floorplan is considered ready for the placement and routing stage.
# Placement, Routing & Standard Cell Characterization

## Placement and Routing Stage in the Physical Design Flow

### 1. Bind Netlist with Physical Cells

Every gate in a circuit has a function, but physically, it's represented as a **box** — with defined width and height. Each component in the design is assigned proper physical dimensions and shape based on this.

The **library** stores all this information for each cell, including:

- Width and height of each cell
- Required operating conditions for the cell
- Various physical shapes for a given gate
- Timing information

A general rule: **the bigger the cell size, the lower its resistance.**

In short, the library holds everything needed for a cell — its shape, size, and timing data.

### 2. Placement

Once the floorplan is finalized, the next step is placing the netlist cells within it. Cells are placed close to the input/output pins they're associated with, to keep connections efficient.

### 3. Optimize Placement

At this stage, wire length and capacitance are estimated, and **repeaters** (buffers) are inserted where needed to maintain **signal integrity**.

- Buffers replicate the signal across long wires.
- Adding more repeaters improves signal integrity but increases area utilization — so it's a trade-off.
- Signal integrity depends directly on wire length and capacitance.

**Slew** (signal transition time) also depends on capacitance:
- Higher capacitance → more charge needed → worse (slower) slew.

**Setup timing analysis** is performed at this stage to verify that the placement meets the required timing specifications.

---

## Need for Characterization

### Standard IC Design Flow

Every chip design must go through this sequence:

1. **Logic Synthesis** — Converts the design's functionality into legal hardware (a gate-level netlist).
2. **Floor Planning** — Takes the netlist from synthesis and decides the size of the core and die. This step depends entirely on the output of logic synthesis.
3. **Placement** — Places the logic cells within the core to meet timing requirements.
4. **CTS (Clock Tree Synthesis)** — Ensures every logic element receives the clock at exactly the same time (zero skew) — a critical step.
5. **Routing** — Connects the placed cells, factoring in specific cell properties.
6. **STA (Static Timing Analysis)** — The final stage of the IC design flow, verifying overall timing.

---

## Cell Design Flow

Standard cells reside in a **library** — a repository containing cells of different functionalities, threshold voltages, dimensions, and more.

The cell design flow has three parts:

### 1. Inputs

- **PDK** (Process Design Kit) — provided by the foundry; all designs must follow it.
- **DRC & LVS rules**
- **SPICE models**
- **Library** and **user-defined specifications**

### 2. Design Steps

- **Circuit Design** — Implement the desired function, then model it.
- **Layout Design**
- **Characterization**

### 3. Outputs

- **CDL** (Circuit Description Language)
- **GDSII**
- **LEF**
- **Extracted SPICE netlist**
- **Timing, noise, and power data**
- **.lib files**
- **Function**

---

## Characterization Flow

The characterization process follows these steps in order:

1. Read the **model files** and **technology (tech) file**.
2. Read the **extracted netlist** file from SPICE.
3. Define/recognize the **behavior of the buffer**.
4. Read the **sub-circuit** of the inverter.
5. Attach the necessary **power supplies**.
6. Apply the **stimulus** (input signal).
7. Provide the necessary **output capacitance**.
8. Provide the necessary **simulation commands**.
9. Feed all these inputs as a characterization file into a configurable software tool called **GUNA**.

### Output from GUNA

The characterization software (GUNA) produces:

- Timing data
- Noise data
- `.lib` files
- Function information


# Section 2 - Lab Implementation :  
  

### Task 1 : Run "picorv32a" Design Floorplanning using OpenLane flow.
<img width="1920" height="983" alt="Screenshot from 2026-07-12 22-40-55" src="https://github.com/user-attachments/assets/137551f2-b2d6-4149-b854-46da14cf7a61" />

<img width="1920" height="983" alt="Screenshot from 2026-07-12 22-42-38" src="https://github.com/user-attachments/assets/6afcbafd-11ef-460e-bc3d-d007228282ca" />
### Task 2 : Calculate the Die area in microns from the values in Floorplan def file.

<img width="1920" height="983" alt="Screenshot from 2026-07-12 22-53-18" src="https://github.com/user-attachments/assets/09ee0751-38b0-4737-a760-1628a39c65cd" />




### Task 3 : Load generated floorplan def in magic tool and explore the floorplan.


<img width="1920" height="983" alt="Screenshot from 2026-07-12 23-02-52" src="https://github.com/user-attachments/assets/59fac81f-e620-483d-9493-5d0f31f841ee" />
<img width="1920" height="983" alt="Screenshot from 2026-07-12 23-08-06" src="https://github.com/user-attachments/assets/c440f15f-072f-456d-8b3d-e2d12480f64e" />
<img width="1920" height="983" alt="Screenshot from 2026-07-12 23-09-55" src="https://github.com/user-attachments/assets/b0acca00-d143-4a8d-98c4-60f6d98611a9" />



### Task 4 : Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.



<img width="1920" height="983" alt="Screenshot from 2026-07-12 23-40-23" src="https://github.com/user-attachments/assets/8fdfc205-8270-46bd-bcaa-40d2269d19d0" />


### Task 5 : Load generated placement def in magic tool and explore the placement.

<img width="1920" height="983" alt="Screenshot from 2026-07-12 23-50-59" src="https://github.com/user-attachments/assets/0d86d573-4c2e-4a80-87a8-40e207870542" />








<img width="1920" height="983" alt="Screenshot from 2026-07-12 23-53-54" src="https://github.com/user-attachments/assets/c75a5657-3973-43ee-a3db-ce7bb170ad60" />

the above image shows the placement of the standard cells

# Sky130 Day 3 - Design Library Cell using Magic Layout and ngspice Characterization

## VTC – SPICE Simulations

### Creating the SPICE Deck
The first step in SPICE simulation is building the **SPICE deck** — this contains all the connectivity information: components, their connections, and the inputs to be provided.

**1. Component connectivity**
Defines how each component (transistor) is connected to every other node in the circuit.

**2. Component values**
- Ideally, the PMOS should be sized 2–3x wider than the NMOS (to balance mobility differences between electrons and holes).
- Output capacitance needs to be defined — arrived at after careful calculation.
- Gate voltage, drain voltage, and supply voltage also need to be defined.

**3. Identify nodes**
Nodes must be identified, since they're required to define the netlist.

**4. Name nodes**
Each identified node is given a name for reference in the netlist.

### Writing the SPICE Deck
Any line starting with `*` is treated as a comment.

Example:
```spice
M1 out in vdd vdd pmos W=0.375u L=0.25u
M2 out in 0   0   nmos W=0.375u L=0.25u
```

The transistor definition follows the order **D G S S**:
- **D** – Drain
- **G** – Gate
- **S** – Source
- **S** – Substrate/Body

**Simulation commands:**
```spice
.op
.dc Vin 0 2.5 0.05
```
This sweeps the input voltage from 0V to 2.5V in steps of 0.05V.

The final step is to reference the model file:
```spice
.LIB "tsmc_025um_model.mod" CMOS_MODELS
.end
```

### Running the SPICE Simulation
- With NMOS and PMOS of the **same width**, the VTC (Voltage Transfer Characteristic) waveform is slightly shifted to the left.
- Increasing the PMOS width to **2.5x** the NMOS width shifts the curve to the center of the graph — this reflects a more balanced (robust) CMOS inverter.
- The overall shape of the waveform stays the same in both cases; only the switching point shifts.
- **Switching threshold (Vm)** is the input voltage at which the output switches states.
- If both NMOS and PMOS are ON simultaneously (during switching), there's a possibility of **leakage/short-circuit current**.
- A **pulse** waveform is time-varying — e.g., a pulse defined from 0.0V to 2.5V has its own rise time and fall time parameters.

---

## CMOS Fabrication: The 16-Mask Process

### 1. Selecting the Substrate
- The layout eventually gets fabricated on a **substrate**.
- Most chips use a **P-type silicon substrate**:
  - High resistivity: 5–50 Ω·cm
  - Doping level: ~10¹⁵ cm⁻³
  - Orientation: (100)
- The substrate must be **less doped than the wells**. Wells are the regions used to fabricate the NMOS and PMOS transistors.

### 2. Creating Active Regions for Transistors
- The active regions (where NMOS/PMOS sit) are sometimes called "buckets," and connections to them happen at the top.
- These buckets must be **isolated from each other** so they don't interfere electrically.

**Isolation process:**
1. Grow a thin ~30nm silicon dioxide layer, followed by an ~80nm silicon nitride layer.
2. Apply a photoresist layer (~1 micron) on top of the substrate.
3. This patterned layout is called **Mask 1** in fabrication terms.

- To protect a region from UV exposure (so no chemical reaction occurs underneath the mask), that area is masked before UV exposure.
- The unexposed resist is washed away in a developing solution, then the mask is removed.
- The nitride layer is etched away.
- The wafer then goes into an **oxidation furnace** (very high temperature) to grow a field oxide layer.
- This process is called **LOCOS** (Local Oxidation of Silicon), and it forms the isolation region between transistors — ensuring they don't electrically communicate with each other.

### 3. N-Well and P-Well Formation
- **N-well** → region where PMOS is built
- **P-well** → region where NMOS is built
- Both wells can't be formed simultaneously — one region is protected (masked) while the other is fabricated, and vice versa.

**Process:**
1. Apply mask, expose to UV light, wash out exposed resist, remove mask.
2. **P-well**: Boron is diffused into the substrate via **ion implantation** (~200 KeV) — high energy is needed so it penetrates through the oxide layer into the substrate.
3. **N-well**: Phosphorus is used instead of boron. The implant energy is higher than boron's because the phosphorus atom is larger.
4. The wafer is then placed in a **drive-in furnace** for an extended period to diffuse the dopants further into the substrate.

This overall approach — forming both wells this way — is known as the **twin-tub process**: PMOS is built in the N-well, NMOS is built in the P-well.

### 4. Formation of the Gate
- The gate is the most critical terminal — it controls the **threshold voltage** (turn-on voltage) of the transistor.
- Threshold voltage depends on the **body effect coefficient (γ, gamma)**, which itself depends on doping concentration and oxide capacitance.
- During fabrication, doping concentration, oxide capacitance, and electron charge are all tuned to achieve the desired threshold voltage.

**Process:**
1. Same steps as before: mask → photoresist → UV exposure.
2. A boron implant is deposited on the substrate surface at a reduced energy (~60 KeV) for the NMOS gate region.
3. Similarly processed for the PMOS gate region.
4. The oxide damaged by ion implantation is etched away using dilute hydrofluoric acid (HF) solution, then regrown to form a high-quality ~10nm gate oxide.
5. A **polysilicon** layer is deposited on top.
6. Since the gate region needs low resistance, it's heavily doped — achieved through another photoresist/etch cycle — leaving the patterned **polysilicon gate**.

### 5. Lightly Doped Drain (LDD) Formation
LDD regions (P⁻ and N⁻, "lightly doped") are added to counter two effects:

- **Hot electron effect**: High-energy carriers can break Si–Si bonds if they cross the ~3.2eV barrier into the conduction band, causing reliability issues.
- **Short channel effect**: As device size shrinks, the drain voltage can penetrate into the channel region.

**Process:**
1. Mask → photoresist → UV exposure on the relevant region.
2. Implant N-type impurity at carefully chosen (low) energy so it doesn't penetrate too deep.
3. Repeat the equivalent process for the other MOS type.
4. Deposit a SiO₂ layer, then use plasma anisotropic etching — this leaves oxide remaining only on the sidewalls, forming **sidewall spacers** used to define the LDD regions.

### 6. Source and Drain Formation
1. Add a thin oxide layer (screen oxide).
2. Same mask → photoresist → UV process.
3. Implant **arsenic** (~75 KeV) into the N-implant region (within the P-well).
4. Implant **boron** (~50 KeV) into the P-implant region (within the N-well).
5. **Anneal** the wafer (high-temperature drive-in) to diffuse the implanted impurities properly.

### 7. Contacts and Interconnect Formation
1. Remove the thin screen oxide using HF solution to expose the gate, source, and drain surfaces.
2. Deposit **titanium** on the wafer surface via **sputtering** (bombarding a titanium target with argon gas to displace Ti atoms onto the wafer).
3. Heat the wafer to ~700°C in an N₂ (nitrogen) ambient for ~60 seconds — this reacts the titanium with the underlying silicon to form **low-resistance TiSi₂** at the contacts.
4. **TiN** (titanium nitride) is used for local interconnects between nearby contacts.
5. TiN is patterned using the standard mask/photoresist/UV steps, then etched using **RCA cleaning** — a solution of de-ionized water, ammonium hydroxide, and hydrogen peroxide.

### 8. Higher-Level Metal Formation
Since the existing surface topography is too uneven for direct metal routing:

1. Deposit a thick layer of **SiO₂ doped with phosphorus or boron** — known as **PSG (Phosphosilicate Glass)** or **BPSG (Borophosphosilicate Glass)**.
2. **Chemical Mechanical Polishing (CMP)** is used to planarize (flatten) the wafer surface.
3. Drill contact holes using the standard photolithography steps.
4. Remove photoresist, then deposit a thin TiN layer.
5. Deposit a blanket **tungsten (W)** layer to fill the contact holes.
6. Use CMP again to remove excess tungsten.
7. Deposit an **aluminum (Al)** layer, pattern it via photolithography, and etch it using **plasma etching**.
8. Repeat the contact-hole patterning process for the next metal level.
9. Deposit a thin TiN layer again, followed by tungsten (W) as contacts for the next level.
10. Finally, deposit a top dielectric layer of **Si₃N₄ (silicon nitride)** to protect the finished chip.

---

## Introduction to Magic
To learn more about the Magic layout tool, refer to the **opencircuitdesign** website. The **technology file** is the core file that tells Magic everything about the process (layers, design rules, etc.) it's working with.

# Section-3 Lab Implementation 

## Task - 1 : Cloning custom inverter standard cell design from github repository: 


The custom inverter layout used for this lab is provided in a separate repository by Nickson Jose. We clone it into our OpenLANE working directory and copy over the Sky130 technology file so Magic can interpret the layout correctly.

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

**What this does:**
- Clones the pre-built custom inverter cell (`sky130_inv.mag`) from Nickson Jose's repo — this is the standard cell we'll be examining and characterizing through the rest of Day 3.
- Copies the `sky130A.tech` file into the same directory so Magic has direct access to the Sky130 technology rules without needing a separate path reference.
- `ls` is just a sanity check to confirm the `.mag` layout file and tech file are both present before opening Magic.
- The final command launches Magic with the Sky130 tech file loaded, opening the custom inverter layout for inspection.



<img width="1920" height="1080" alt="Screenshot from 2026-07-15 19-20-35" src="https://github.com/user-attachments/assets/bcd290e8-496a-47a2-8d42-7e7ea893e227" />

The above shows the screenshot of the commands used


## Task - 2 : Load a custom inverter layout in magic and explore : 

<img width="1920" height="1080" alt="Screenshot from 2026-07-15 19-21-51" src="https://github.com/user-attachments/assets/64d0a2e9-f161-43c4-9e6e-97067db14d8d" />

The above image shows the custom layout of the inverter

<img width="1920" height="1080" alt="Screenshot from 2026-07-15 19-26-30" src="https://github.com/user-attachments/assets/17a0a9b0-71b2-48a4-8aa0-053d7c14abd9" />

Identified the polysilicon gate, and nmos

<img width="1920" height="1080" alt="Screenshot from 2026-07-15 19-29-07" src="https://github.com/user-attachments/assets/dfed9227-9932-4637-8331-6bf8fbc9e8da" />

both the nnmos and pmos drain is connected to the ouput

<img width="1920" height="1080" alt="Screenshot from 2026-07-15 19-30-08" src="https://github.com/user-attachments/assets/1e0ac88f-7a16-48d1-90d7-21b15c172afb" />

both the nmos and pmmos polysilicon gate is connected to the input


## Task - 3 : Extraction of spice file from the magic tool

```bash
#first we have to check the directory
pwd
# this command is to extract in .ext format
extract all
# this command enables the parasitic extraction also
ext2spice cthresh0 rthresh0
# this command converts the ext to spice format
ext2spice
```

<img width="1920" height="983" alt="Screenshot from 2026-07-15 19-46-07" src="https://github.com/user-attachments/assets/9f5950fe-b24f-47d0-82df-7423bc4efbc9" />



The below shows the extracted spice file

<img width="1920" height="983" alt="Screenshot from 2026-07-15 19-52-30" src="https://github.com/user-attachments/assets/20dbf5a1-61ff-42d8-8f60-1d584a89b3dc" />


## Task - 4 : Measuring unit distance in the layout grid

<img width="1920" height="983" alt="Screenshot from 2026-07-15 20-08-16" src="https://github.com/user-attachments/assets/3d7a795d-da27-4bd3-b4f2-c794b447468e" />


## Task - 5 : Post layout ngspice Simulation 

```bash
#in the same directory
ngspice sky130_inv.spice
#now load the spice plot
plot y vs time a

```


<img width="1920" height="983" alt="Screenshot from 2026-07-15 20-33-27" src="https://github.com/user-attachments/assets/75a41a21-eebf-4f11-9f90-36312b9f0737" />



<img width="1920" height="983" alt="Screenshot from 2026-07-15 20-33-44" src="https://github.com/user-attachments/assets/757e4f21-29b9-4319-b0d6-3e6a0165f0a5" />



## Rise Transition Time Calculation

The rise transition time is calculated as:

\[
\text{Rise Transition Time} = \text{Time taken for output to rise to 80\%} - \text{Time taken for output to rise to 20\%}
\]

Given:

- **20% of output** = **660 mV**
- **80% of output** = **2.64 V**

### 20% Screenshot

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ef56094f-f29e-447d-800f-4864792ebe4a" />

### 80% Screenshots
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/34311928-0033-42a8-8e6b-e0f166bde500" />


## Rise Transition Time Calculation

The rise transition time is calculated as:

\[
\text{Rise Transition Time} = \text{Time taken for output to rise to 80\%} - \text{Time taken for output to rise to 20\%}
\]

\[
\text{Rise Transition Time} = 2.24638 - 2.18242 = 0.06396\ \text{ns} = 63.96\ \text{ps}
\]

---

## Fall Transition Time Calculation

The fall transition time is calculated as:

\[
\text{Fall Transition Time} = \text{Time taken for output to fall to 20\%} - \text{Time taken for output to fall to 80\%}
\]

Given:

- **20% of output** = **660 mV**
- **80% of output** = **2.64 V**

### 20% Screenshot

*(Insert the 20% waveform screenshot here)*
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1fea3a1b-a375-4418-bfbf-1e14dd2e0e9c" />
### 80% Screenshot
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ba41b7d4-dee8-4fdd-9d7c-5b9a9cf5a5b7" />

## Fall Transition Time Calculation

The fall transition time is calculated as:

\[
\text{Fall Transition Time} = \text{Time taken for output to fall to 20\%} - \text{Time taken for output to fall to 80\%}
\]

\[
\text{Fall Transition Time} = 4.0955 - 4.0536 = 0.0419\ \text{ns} = 41.9\ \text{ps}
\]

---

## Rise Cell Delay Calculation

The rise cell delay is calculated as:

\[
\text{Rise Cell Delay} = \text{Time taken for output to rise to 50\%} - \text{Time taken for input to fall to 50\%}
\]

Given:

- **50% of 3.3 V** = **1.65 V**

### 50% Screenshots

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7beb7ef8-1d45-4a9a-b995-a7db0bbe572d" />


## Rise Cell Delay Calculation

The rise cell delay is calculated as:

\[
\text{Rise Cell Delay} = \text{Time taken for output to rise to 50\%} - \text{Time taken for input to fall to 50\%}
\]

\[
\text{Rise Cell Delay} = 2.21144 - 2.15008 = 0.06136\ \text{ns} = 61.36\ \text{ps}
\]

---

## Fall Cell Delay Calculation

The fall cell delay is calculated as:

\[
\text{Fall Cell Delay} = \text{Time taken for output to fall to 50\%} - \text{Time taken for input to rise to 50\%}
\]

Given:

- **50% of 3.3 V** = **1.65 V**

### 50% Screenshots

*(Insert the 50% input and output waveform screenshots here)*
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/931ab2f6-1acd-4c6e-85b3-638915c43a2c" />


## Task - 5 : Lab Exercise to fix the poly.9 error in sky130.tech file
















<img width="1920" height="1080" alt="Screenshot from 2026-07-15 23-24-23" src="https://github.com/user-attachments/assets/928da76a-9640-48b5-9f1a-9c69074b8207" />

























<img width="1920" height="1080" alt="Screenshot from 2026-07-15 23-24-58" src="https://github.com/user-attachments/assets/25c56f3a-0060-41ef-902e-e81b1139ece4" />





























modifying the tech file by adding the new rule
<img width="1920" height="1080" alt="Screenshot from 2026-07-15 23-54-00" src="https://github.com/user-attachments/assets/856bdc48-03b2-41e8-83d5-d4b601763a45" />

<img width="1920" height="1080" alt="Screenshot from 2026-07-15 23-54-27" src="https://github.com/user-attachments/assets/63632bbd-12b8-43c7-8cf7-c3aa72bb5263" />

after that again loading the sky130A.tech file in the tkcon window


<img width="1920" height="1080" alt="Screenshot from 2026-07-15 23-55-27" src="https://github.com/user-attachments/assets/9160940c-f9f7-4e10-9fbb-262e3cfaaf3a" />


# Sky130 Day 4 - Pre-layout timing analysis and importance of good clock tree

Now we're going to extract the LEF file of this, 
### In a PnR workflow, we must follow the below three guidelines : 
1. The input and output ports lies in the intersection of the vertical and horizonal tracks.
2. The width of the standard cell should be odd multiples of the track pitch.
3. Height of the standard cell should be even multiples of the vertical track pitch.


Commands to open the custom inverter layout
```bash
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &

```

<img width="1920" height="983" alt="Screenshot from 2026-07-16 19-34-23" src="https://github.com/user-attachments/assets/5bad3bef-6fcf-421a-9af8-341c6dbb24d3" />

The below screenshot shows the tracks.info of sky130_fd_sc_hd
<img width="1920" height="983" alt="Screenshot from 2026-07-16 19-23-50" src="https://github.com/user-attachments/assets/52801fff-1be7-433d-8ad4-9de5dd1de104" />

The below is the commands for tkcon window to set grid as tracks of locali layer

```bash
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```
<img width="1920" height="983" alt="Screenshot from 2026-07-16 19-37-01" src="https://github.com/user-attachments/assets/41713ba3-0ffa-4e04-a834-04b4ecabad97" />

