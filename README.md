# NASSCOM-VSD-SoC-Design
Digital VLSI SoC design and planning workshop with complete RTL2GDSII flow organised by VSD in collaboration with NASSCOM (Advanced Physical Design using OpenLANE/Sky130)

## SKY130_D1_SK2 - SoC design and
OpenLANE

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

## SKY130_D1_SK3 - Get familiar to open-source EDA tools

### SKY_L1 - OpenLANE Directory structure in detail
  This module explains the OpenLane tool, the directory , the command, the environment of the OpenLane
  How to invoke and run the tool
  key linux command such as : 
      ls - listing
      ls -ltr - list everything in the chronological order
      cd - change Directory
      less  - open
      clear - to clear the terminal
  to know about the command
      command_name --help

  Directory of OpenLane : 

  cd /Desktop/work/tools/openlane_working_dir


  OpenLane Directory(  ) : 
   


  libs.ref => itcontains the files specific to the pdk
  libs.tech => it contains the file specific to the technology (i.e) ngspice, openLane, magic

  PDK(Proces Development Kit):
      the folder has the all information of the pdk, we are using a sky130nm pdk, which is opensource
      openlane is built around the pdk

### SKY_L2 - Design Preparation Step
we have to run in the interactive mode, or else it will process everything automatically
then, import the packages



all the designs are from the design folder from the openlane, 
src file for source contains verilog, sdc information
config.tcl bypasses any configuration that is already default, override the settings 
sky130Axx file contains default value from the OpenLane. it won't affect the flow if we have not this file



before synthesis we have to setup file system , 
design setup stage
command prep -design picorv32a

### SKY_L3 - Review files after design prep and run synthesis

before running, a new file is created on our design file
from the runs folder
today date will be created
      
tmp will be empty
result folder will have the result of the synthesis and etc
reports folder have the rpts of every step
config.tcl have the default parameters
commands file have the commands we use
this is the file created on the merge LIF 


then we have to run_synthesis


### SKY_L4 - OpenLANE Project Git Link Description

recommend yt videos to know more about the openlane : 
  fossi dialup
    an intro to openlane skywater pdk
github repo : 
  efabless/openlane
  all the information about the OpenLane


### SKY_L5 - Steps to characterize synthesis results

The first objective is to calculate the flop ratio
which is the D flip flop of the cell
The formula is , 
Total Dff cell / Number of cells * 100
it is the flop ratio

The files will be added on the synthesis and the report folders

Lab Implemention : 

# Running the OpenLANE Flow (Interactive Mode)

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

    The task is to find the flop ratio from the synthesis statistics report file
    
