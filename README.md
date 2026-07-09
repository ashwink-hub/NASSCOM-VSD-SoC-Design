# NASSCOM-VSD-SoC-Design
Digital VLSI SoC design and planning workshop with complete RTL2GDSII flow organised by VSD in collaboration with NASSCOM (Advanced Physical Design using OpenLANE/Sky130)

## SKY130_D1_SK2 - SoC design and OpenLANE

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

Move into the folder where OpenLANE is installed and set up.

## Step 2: Enter the OpenLANE Docker Container

```bash
# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
docker
```

OpenLANE runs inside a Docker container so that all its tools and dependencies work the same way on any machine. To avoid typing that long `docker run` command every time, it's usually saved as an alias called `docker`. Once the alias is set, simply typing `docker` drops you into the OpenLANE container, with your current folder mounted inside it so files can be shared between your machine and the container.

## Step 3: Launch OpenLANE in Interactive Mode

```bash
./flow.tcl -interactive
```

This starts the OpenLANE flow, but instead of running everything automatically end-to-end, it opens an interactive shell where you can run each stage of the flow step by step. This is helpful for learning the flow or debugging a specific stage.

## Step 4: Load the OpenLANE Package

```bash
package require openlane 0.9
```

This loads the OpenLANE Tcl package (version 0.9) so all the flow commands become available for use.

## Step 5: Prep the Design

```bash
prep -design picorv32a
```

Before running any stage of the flow, the design needs to be "prepped." This command sets up the required directories, merges the PDK and design-specific configuration files, and creates a fresh run folder to store all the outputs for this particular run. Here, we're prepping the `picorv32a` design.

## Step 6: Run Synthesis

```bash
run_synthesis
```

This runs the RTL synthesis stage, converting the design's RTL (written in Verilog) into a gate-level netlist made up of standard cells from the PDK library.

## Step 7: Exit OpenLANE

```bash
exit
```

Closes the interactive OpenLANE flow session.

## Step 8: Exit the Docker Container

```bash
exit
```

Closes the Docker container and returns you to your regular terminal.

    
