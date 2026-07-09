# NASSCOM-VSD-SoC-Design
Digital VLSI SoC design and planning workshop with complete RTL2GDSII flow organised by VSD in collaboration with NASSCOM (Advanced Physical Design using OpenLANE/Sky130)

## SKY130_D1_SK2 - SoC design and
OpenLANE

### SKY_L2 - Simplified RTL2GDS flow :

<!-- image -->

The above image is the simplified RTL Design flow
The major step is the synthesis
It converts the RTL code into a standard cell library

<!-- image -->

In the floor planning,

<!-- image -->

In chip floor planning the chip die is partitoned between different components

<!-- image -->

In this step, macro rows and routing steps were defined, which will be used later during pnr

<!-- image -->

In power planning, The power network is constructed, typically the chip is powered by vdd and
gnd pins
The power pins are the connected to all components, such parallel instructions are meant to
reduce the resistance
And to address the electro migration problem

<!-- image -->

Typically cell placement is done using two steps :
Global and Detailed Placement
Global placement finds the optimum position for all cells, it may not be legal, so cells may
overlap
In details placement, the positions obtained from the global placement is altered to be legal

<!-- image -->

After placement, comes routing, before routing we should create the clock distribution network

<!-- image -->

After this, comes the signal routing using horizontal and vertical nets
THE SKY130 PDK CONTAINS THE SIX ROUTING LAYERS

<!-- image -->

mostly routing grids are used as global and detailed routing,
Once routing is finished, we construct the final layout

<!-- image -->

The final layout should undergo the above verification process
Atlast, timing analysis is done to check the layout running according to the specific timing

### SKY_L3 - Introduction to OpenLANE
and strive chipsets

<!-- image -->

It is opensource and free

<!-- image -->

The below is the strive Soc family

<!-- image -->

<!-- image -->

OpenLane can be used to generate macros and chips like the final layout
It has the two modes of operation :
Autonomous and Interative

<!-- image -->

It comes with 43 best design examples and so on

### SKY_L4 - Introduction to OpenLane
detailed ASIC design flow

The below diagram shows the openLane flow

<!-- image -->

OpenLane is based on several opensource projects

<!-- image -->

It has the several process for the testing the design ,

<!-- image -->

After testing comes the physical Implementation, which is completely run by OpenRoad

<!-- image -->

The above process are done in the openRoad
The input to this process is the gate level netlist which is prepared after the synthesis

<!-- image -->

After the netlist is prepared the logic verification test should be carried out
The main reason for the LEC test is to confirm that the function did not change after modifying
the netlist

Dealing with the Antenna Rule Violation

<!-- image -->

It damages the transistor gates during fabrication
There is two solution with deal with this problem
1. Bridging

<!-- image -->

2. Adding antena diode

<!-- image -->

In openLance, we take the preventive approach

<!-- image -->

The open sta from the openroad is used to check the timing violation(Static Timing Analysis)
And the physical verification of DRC and LVS is checked using the Magic Tool

<!-- image -->
