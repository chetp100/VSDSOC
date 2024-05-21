# VSD SoC design Program
# Contents
Table Of Contents
1. Introduction to Open-Source EDA, OpenLANE, and Sky130 PDK
a) Open-Source EDA Tools
b) Electronic Design Automation (EDA): Software for designing electronic systems, especially integrated circuits (ICs).
c) Open-source EDA tools: Provide affordable, adaptable, and collaborative environments for IC design.
**OpenLANE**
OpenLANE: An open-source ASIC (Application-Specific Integrated Circuit) design flow that integrates several EDA tools to convert RTL (Register Transfer Level) code to GDSII (layout format).
Sky130 PDK: A 130nm technology node Process Design Kit developed by Google and SkyWater Technology, available for free to facilitate open-source IC design.
Overview of Open-Source Digital ASIC Design Components
RTL Design: Writing hardware descriptions using languages like Verilog or VHDL.
Synthesis: Translating RTL code into a gate-level netlist.
Floorplanning: Laying out the major functional blocks on the chip.
Placement: Positioning the standard cells in the defined layout.
Clock Tree Synthesis (CTS): Creating a clock distribution network.
Routing: Connecting all the placed cells and blocks.
Signoff: Performing final checks including timing analysis, DRC (Design Rule Check), and LVS (Layout vs. Schematic).
Simplified RTL2GDS Flow
RTL (Verilog): Start with your RTL design.
Synthesis: Use tools like Yosys to convert RTL to a gate-level netlist.
Floorplanning: Define the chip's layout.
Placement: Place standard cells according to the floorplan.
CTS: Design the clock distribution network.
Routing: Connect all cells and blocks.
DRC/LVS: Check for design rule compliance and logical correctness.
GDSII: Generate the final layout file for fabrication.
Detailed ASIC Design Flow Using OpenLANE
Synthesis
Tool: Yosys
Goal: Convert RTL code into a gate-level netlist.
Process: Load RTL, set constraints, and run synthesis to generate the netlist.
2. Floorplanning and Placement
Running Floorplan with OpenLANE
Prepare Design: Ensure the synthesized netlist is ready.
Initialize Floorplan: Execute the floorplanning command in OpenLANE.
Set Constraints: Define the power grid, I/O pins, and blockages.
Run Floorplan: Generate the initial layout using the floorplanning tool.
Reviewing Floorplan Files and Viewing Floorplan
Check Output Files: Review floorplan.def, floorplan.log, and floorplan.lef.
View Layout: Use tools like Magic or KLayout to inspect the floorplan.
Running Placement with OpenLANE
Initialize Placement: Begin the placement step after floorplanning.
Set Constraints: Define specific placement constraints if needed.
Run Placement: Use the placement tool to position the standard cells.
3. Design Library Cell with Magic Layout and Ngspice Characterization
CMOS Inverter Simulation with Ngspice
Create Schematic: Design the CMOS inverter.
Simulate: Perform DC, AC, and transient analysis using Ngspice.
Extracting Spice Netlist from Standard Cell Layout
Layout in Magic: Draw the layout of the standard cell.
Extract Netlist: Use Magic to generate the spice netlist from the layout.
Characterizing the Inverter Using Sky130 Model Files
Setup: Ensure Sky130 model files are available.
Simulate: Use Ngspice to run simulations and extract performance metrics.
Lab Challenge: Describing DRC Errors
Identify Errors: Use Magic to find design rule violations.
Describe Errors: Document and explain DRC errors as geometrical constructs.
4. Pre-Layout Timing Analysis and Clock Tree Synthesis
Converting Magic Layout to Standard Cell LEF
Complete Layout: Ensure the layout is finished in Magic.
Export LEF: Use Magic to convert the layout to a LEF file.
Configuring Synthesis to Fix Slack and Include VSDINV
Adjust Constraints: Modify synthesis settings to improve timing slack.
Include VSDINV: Ensure the inverter cell is included in the synthesis process.
Timing Analysis with OpenSTA
Run OpenSTA: Load the design and perform static timing analysis to identify timing issues.
Post-CTS Timing Analysis with OpenROAD
Clock Tree Synthesis: Use TritonCTS to design the clock tree.
Timing Analysis: Perform post-CTS timing analysis using OpenROAD.
Clock Tree Synthesis with TritonCTS and Signal Integrity
Design Clock Tree: Utilize TritonCTS for clock tree design.
Verify Integrity: Check clock signal integrity and timing.
5. Final Steps for RTL2GDS Using TritonRoute and OpenSTA
Power Distribution Network and Routing
Power Planning: Design the power distribution network.
Routing with TritonRoute: Perform detailed routing to connect all components.
Final Timing Analysis: Use OpenSTA for the final timing verification.
Generate GDSII: Create the final GDSII file for chip fabrication.
# Day-01
# Inception of open-source EDA, OpenLANE and Sky130 PDK
##  How to talk to computers
###   Introduction to QFN-48 Package, chip, pads, core, die and IPs
In the first session of video lecture, we learnt about a proceessor and its interfaces. The dimensions of the entire processor was 7mm x 7mm. The different types of interfaces include Pads, Core, Die .
The definitions are as follows:
Pads- This Send signal inside to the chip.
Core- It consists of the Logic gates.
Die - It is the size of the entire chip.
the Example given to us for our learning was RISC-V.
# Lab 01
Directory of OPENLANE:
![1 image](https://github.com/chetp100/VSDSOC/assets/169384940/f30a048d-04ca-4c19-bbeb-b4b65be5582e)
The directory to get into the openlane is as follows:
cd Desktop/work/tools/openlane_working_dir/openlane
<br>
Then enter into docker file
<br>
For beginning the session enter as ./flow.tcl -interactive
<br>
**The next stage is Design Preparation stage**
<br>
Let us first enter our Desired package 
<br>
The command is % package require openlane 0.9
<br>
For preparation the command is prep -design picorv32a
<br>
![image 2](https://github.com/chetp100/VSDSOC/assets/169384940/4232d60d-4000-45fa-8a3b-121d67b110c7)
<br>
Ones the Complete preparation is done then lets now find the run file in the picorv32a .
<br>
![image 3](https://github.com/chetp100/VSDSOC/assets/169384940/9f7b9283-f610-4c73-adfe-9fb9451ec0b8)
<br>
We can see the date at which we have recently finished our design prepartion step.
<br>
![4 image](https://github.com/chetp100/VSDSOC/assets/169384940/0e278870-17df-4ec3-9795-d60d9105ac0e)
<br>
A temporary folder will be created in the recent date of design preparation step. It is named as tmp file. We can see many sub folders created in tmp file.
<br>
![5 image](https://github.com/chetp100/VSDSOC/assets/169384940/7a713311-fc25-474e-89d0-7ac2b2cc1826)
<br>
The folders in tmp file are as shown:
<br>
![image 6](https://github.com/chetp100/VSDSOC/assets/169384940/f778eca9-979a-455c-835b-2119af1352ad)
<br>
#Synthesis#
<br>
To Synthesis the design the command is run_synthesis
<br>
![image 7](https://github.com/chetp100/VSDSOC/assets/169384940/dbc6991c-7f2e-412c-8769-1f06e0839ec3)
<br>
Then complete synthesis process takes place then the synthesis complete appears on the screen.
<br>
![image 8](https://github.com/chetp100/VSDSOC/assets/169384940/58d2d9ed-0828-4227-8868-3a0bd9a1af41)
<br>
**Utilisation Factor**
<br>
The flip flop ratio is defined as the number of flip flops divided by the total number of cells
<br>
![image 8 g](https://github.com/chetp100/VSDSOC/assets/169384940/e6181776-cc66-455a-b21c-caa846cb667e)
<br>
Here we can see No.of flipflops as 1613
<br>
Total No.of cells is 14876
<br>
Flip Flop Ratio is 1613/14876 = 0.1084

<br>

## **DAY 2**
## FLOOR PLANNING 
### UTILISATION FACTOR
<br>
The Utlisation factor is defined as the total area of Netlist to the Area of the Core.
<br>

### ASPECT RATIO
It is defined as the ratio of the height and width of the element box.
<br>

### FLOOR PLANNING
The arrangement of the Intellectual Properties (IP's) in a chip is reffered as Floor Planning. These are called as pre-placed cells because these are placed in a chip before automated placement and routing is done.
<br>
These are implemented once, used multiple times.
<br>

### The Steps to run Floorplan in OpenLane

The command that need to be typed is *run_floorplan*
<br>
![9](https://github.com/chetp100/VSDSOC/assets/169384940/2b8b2e4b-e30b-4698-93c2-f16254913d25)
<br>
After complete Floorplan The line *PND generation Successfull* appears.
<br>
![10](https://github.com/chetp100/VSDSOC/assets/169384940/f942d386-4c77-4d55-a14b-4ad55411cdcb)
<br>
Its time to view the VMetal nd HMetal (Vertical and Horizontal Metals). The number will be one more than the actual configuratuion.  View in configure.tcl file.
![12](https://github.com/chetp100/VSDSOC/assets/169384940/f7fa5a22-e9df-4518-b1a9-86cec3edac09)
<br>
to view the die area we have to go to the ioplacer in floorplan.
<br>
![14](https://github.com/chetp100/VSDSOC/assets/169384940/e954adb9-22db-4db1-bb96-1a07819e8cde)
<br>
Then the ioplacer folder opens. We can find the total area of the die and the unit distance.
<br>
![13](https://github.com/chetp100/VSDSOC/assets/169384940/081d64fc-ad1e-4004-ac5d-e518b2cd27a6)
<br>
We can observe that the dimension of the die is 660685 x 671405. The unit distance micron is 1000.
<br>
To visualize the floorplanning in the layout we need to open via Magic. The path to go to the magic is 
<br>
```
magic -T /home/vsdsquadron/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef 
  read ../../tmp/merged.lef def read picorv32a.floorplan.def &

```
<br>

![13](https://github.com/chetp100/VSDSOC/assets/169384940/c894dfb0-8fd1-44e3-924f-eb3b42c97b09)
<br>
The Magic Layout appears . To zoom it the steps are 
<br>

Left Click--- Right Click --- Z
<br>
![18](https://github.com/chetp100/VSDSOC/assets/169384940/41ffea54-ec1a-4e00-be15-de5ec1197e87)
<br>
To view the Horizontal and Vertical pins zoom in.
<br>

![20](https://github.com/chetp100/VSDSOC/assets/169384940/db854fa5-0dc9-4d1b-ad72-d5b6968f47c7)
<br>

![22](https://github.com/chetp100/VSDSOC/assets/169384940/e66983d4-b6fb-47ed-8cc8-7ce81301f86a)
<br>

To know more about the pins click on them and type **What**  in the tcon.tcl window
<br>

![21](https://github.com/chetp100/VSDSOC/assets/169384940/95739e18-b7bd-4110-8dcc-fd793e1bc8bb)
<br>

### PLACEMENT

Placement is a very important stage of physical design where all the standard cells get placed inside the core boundary.

<br>

To run the placement in Openlane
```
run_placement

```
![23](https://github.com/chetp100/VSDSOC/assets/169384940/ac3cee96-52ee-409a-817d-e882b51a1999)

<br>

 The Utilization area and Total Area for Utilization in core can be seen.
 <br>
 
 ![24](https://github.com/chetp100/VSDSOC/assets/169384940/fb7b1788-7dd9-4080-95af-f2de909aee9b)
<br>

To view the Layout of Placement in magic go to

```
magic -T /home/vsdsquadron/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef 
  read ../../tmp/merged.lef def read picorv32a.placement.def &

```
![25](https://github.com/chetp100/VSDSOC/assets/169384940/c762aa83-587d-46aa-bf37-aca80920921d)
<br>

Zoom it to see the placed blocks.
<br>

![27](https://github.com/chetp100/VSDSOC/assets/169384940/d502cccc-d3b9-4b30-80fc-cd6349254e52)
<br>

# DAY 03

## DESIGN AND SIMULATION USING MAGIC LAYOUT AND NGSPICE SIMULATION

### CMOS INVERTER

An inverter is a device which inverts the given input and provide the output. Here, we are learning about Inverter using CMOS Technology. The design consists of nfet and pfet transistors. The input is connected to the gates of the transitor and the output is collected from the drains of the tranistor.

### To Gitclone the inverter file

![32](https://github.com/chetp100/VSDSOC/assets/169384940/e4d4e69c-826d-4cdf-aed2-1b43d4ce1769)

<br>
We can now see the Inverter magic file. Now, we will open the magic file using the previous commans to open magic layout.
<br>

![33](https://github.com/chetp100/VSDSOC/assets/169384940/b1b12f03-14ad-4937-9f19-0696dbcc6722)
<br>

The inverter magic layout file opens.
<br>

![34](https://github.com/chetp100/VSDSOC/assets/169384940/d446688f-a529-438a-9437-987150585314)

To know more about the elements in the layout, keep the cursor on the required element and then type 'what' in the top.tcl file. It provides the information of that element.

![35](https://github.com/chetp100/VSDSOC/assets/169384940/adbf0fa0-5a71-4b52-9908-16468ec21876)
<br>

### Extraction of the file and creation of the spice file

For extraction 
```
extract all

```
For creation of spice file 
```
ext2spice cthresh 0 rthresh

```
![38](https://github.com/chetp100/VSDSOC/assets/169384940/bd78f13c-635a-4756-b947-80bf653fdbf3)

Once the extraction is finished , we get the extracted file in the vsdstdcelldesign folder. Then the extraction command appears.
<br>
![39](https://github.com/chetp100/VSDSOC/assets/169384940/50aff627-1640-4b23-8158-0da2ca036eed)

<br>
To open ngspice, type as follows.

![ng2](https://github.com/chetp100/VSDSOC/assets/169384940/bffcea1b-8d79-44d4-8911-48557181e675)


The spice file is generated.

![40](https://github.com/chetp100/VSDSOC/assets/169384940/4f57fafe-a7a5-420f-809a-0b0dcd0d6c18)

Now we need to change the values of the scales and also we should add pmos and nmos libraries.
<br>
The rise time 0.1ns and fall time 2ns of the pulses are added.
![ngspice file](https://github.com/chetp100/VSDSOC/assets/169384940/053d4290-2a5b-4b08-a979-dbfb264a3a8e)

Then the transient analysis is performed.

![ngspice waveform](https://github.com/chetp100/VSDSOC/assets/169384940/88ce9a3e-595e-4711-b4e6-1f76661da882)

Rise time is measured from 20% to 80% of the value.
VDD + 3.3V
20% of is 3.3V is 660mV
80% of 3.3V is 2.64V

To run DRC tests

![drc_test](https://github.com/chetp100/VSDSOC/assets/169384940/5cc50abb-ac2c-4cbf-b927-9a67dabe189e)

to see load error

![LOAD ERROR](https://github.com/chetp100/VSDSOC/assets/169384940/52b36e65-1b22-4ca8-9e58-501975d387e4)

to load poly layer

![POLY LAYER](https://github.com/chetp100/VSDSOC/assets/169384940/e5c91ebe-af0e-4901-b258-b37ce11271ce)

to check drc copies.. to create copies and move it

![drc chexk cpy](https://github.com/chetp100/VSDSOC/assets/169384940/81d36144-0c36-43d6-a358-c0279e66e377)

To check via between metals

![via metAL](https://github.com/chetp100/VSDSOC/assets/169384940/fbaec0c7-a219-40e4-a583-dfd699b1cbeb)

To find distance between via

![DISTANCE BETWEEN VIA](https://github.com/chetp100/VSDSOC/assets/169384940/8d054387-6f69-4cbf-b39b-dec26031b5d9)







<br>


# DAY 04

PRE-LAYOUT TIMING AND CLOCK TREE SYNTHESIS

Creating lef file

![43](https://github.com/chetp100/VSDSOC/assets/169384940/e50b15ef-2a92-410c-85a5-a097229a07c4)
<br>

The file is now available in the picorv32a folder

![44](https://github.com/chetp100/VSDSOC/assets/169384940/5db4b136-893d-4720-9f63-0fffe998e0af)

lef file appears

![45](https://github.com/chetp100/VSDSOC/assets/169384940/266012bd-cd0c-4a2f-943c-f617e2b3d152)

copy this lef file in the src file

![46](https://github.com/chetp100/VSDSOC/assets/169384940/f659fa3d-d064-48ef-ba5b-0fe1854c79e6)

it is now available in the src file. it can be checked in src file

![47](https://github.com/chetp100/VSDSOC/assets/169384940/880f517c-037e-4d38-b1ed-b5ae9d36f426)

Next we have to export all lib files to the scr file

![49](https://github.com/chetp100/VSDSOC/assets/169384940/c9795bd3-39cd-4370-9095-45f610bc7051)

Now, again we have to do 
<br>
Preparation
<br>
run_synthesis
<br>
init_floorplan
<br>
place_io
<br>
tap_decap_or
<br>
run_placement
<br>
![51](https://github.com/chetp100/VSDSOC/assets/169384940/d2ade415-4b4a-4264-98e4-37bf1374786a)

![54](https://github.com/chetp100/VSDSOC/assets/169384940/6a2c896d-290a-4ce2-b897-b3371f91be72)

![55](https://github.com/chetp100/VSDSOC/assets/169384940/755bf859-8890-46ef-a2d4-bdf638d1ea99)

![59](https://github.com/chetp100/VSDSOC/assets/169384940/13e2dd2c-8958-4b4d-a51c-0cda89418562)

![61](https://github.com/chetp100/VSDSOC/assets/169384940/fa7d2aac-4998-4e4d-958d-8724799d02d5)

![62](https://github.com/chetp100/VSDSOC/assets/169384940/7538247a-e512-48d4-911d-f468b75f7c35)

## Configuration in Synthesis window to selesct slack and also adding vsdinv file

![70](https://github.com/chetp100/VSDSOC/assets/169384940/a7879e41-b423-40c0-a0ce-85aa3c5c55ce)
<br>
wns= -23.89 tns== -711.59
<br>
init_floorplan
<br>
place_io
<br>
tap_decap_or
<br>
run_placement
<br>

Now using Magic file, observe the placement and floorplan.

![68](https://github.com/chetp100/VSDSOC/assets/169384940/b22be279-b94e-4f52-aba0-6184c5bcde46)

we can see the inverter placed in the floorplan, if we zoom it.

![69](https://github.com/chetp100/VSDSOC/assets/169384940/96fe2541-61d7-421b-94bf-997356fc7e39)

## Timing Analaysis using openSTA

Run Synthesis function need to be performed.

```
./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

set ::env(SYNTH_SIZING) 1

run_synthesis

```
<br>
In Openlane directory, we need to create pre_sta.conf file.

![VirtualBox_vsdworkshop_21_05_2024_22_49_45](https://github.com/chetp100/VSDSOC/assets/169384940/f3af1756-c704-491d-89ab-6f3538c62645)

In picorv32a/src folder we need to add my_base.sdc file

![72](https://github.com/chetp100/VSDSOC/assets/169384940/7fa156c2-5ba4-4f4b-9631-d0e63275c64e)

now to run sta in Openlane directory we use command

```
sta pre_sta.conf

```
![VirtualBox_vsdworkshop_21_05_2024_22_57_52](https://github.com/chetp100/VSDSOC/assets/169384940/5457c8cd-a79d-42be-9ee3-e887e2a5788d)

<br>

![VirtualBox_vsdworkshop_21_05_2024_22_58_19](https://github.com/chetp100/VSDSOC/assets/169384940/6ad83a30-6446-40b8-90de-0e827bc20ef9)

Here also the worst negative slack is -23.89

For checking the connections to a net

```
report net -connenctions _10566_

```

replace the cell with higher drive strength using  command

```

replace_cell _13165_ sky130_fd_sc_hd__or3_4

```

timing is checked 

```

report_checks -fields {net cap slew input_pins} -digits 4


```
![VirtualBox_vsdworkshop_21_05_2024_23_06_02](https://github.com/chetp100/VSDSOC/assets/169384940/bcef25cc-5754-4f30-9705-3807d5b3a2dc)

We can see the reduction in slack value

## Clock tree synthesis TritonCTS and signal integrity

To create synthesis file

```
write verilog  /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/05-05_10-43/results/synthesis/picorv32a.synthesis.v

```
Run the preparation,floorplan and placement again.

```
prep -design picorv32a -tag 05-05_10-43 -overwrite

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

set ::env(SYNTH_STRATEGY) "DELAY 3"

set ::env(SYNTH_SIZING) 1

run_synthesis

init_floorplan

place_io

tap_decap_or

run_placement

```
now to run the clock tree synthesis

```
run_cts

```

![78](https://github.com/chetp100/VSDSOC/assets/169384940/9ba05277-b3bb-489c-bb14-7b7a26e9391d)

## Post-CTS OpenROAD timing analysis

Using Openroad command


```
openroad

read_lef /openLANE_flow/designs/picorv32a/runs/05-05_10-43/tmp/merged.lef

read_def /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/cts/picorv32a.cts.def

write_db pico_cts.db

read_db pico_cts.db

read_verilog /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock [all_clocks]

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

exit

```
![80](https://github.com/chetp100/VSDSOC/assets/169384940/21443951-6d92-4a3a-af69-6b43c5e504fd)

![82](https://github.com/chetp100/VSDSOC/assets/169384940/2bf1aa52-687d-40f7-8f7f-1bd42f84fdb6)

![84](https://github.com/chetp100/VSDSOC/assets/169384940/4cdf5538-d1f7-431c-961f-9457d69fbd32)

Lab assignment

to replace bigger CTS buffers

commands:

```

set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/placement/picorv32a.placement.def

run_cts

```
![85](https://github.com/chetp100/VSDSOC/assets/169384940/39b2d13c-f2d9-450e-aa10-ca0c12d1b279)

# LAB 05

##  RTL2GDS using tritinRoute and openSTA

First generate PDN file
```
gen_pdn

```

then using magic file command in tmp/floorplan folder run it to see the floorplanning

![VirtualBox_vsdworkshop_21_05_2024_23_29_12](https://github.com/chetp100/VSDSOC/assets/169384940/6607ef0a-bef0-4dd4-a252-2f321acb3851)

![Screenshot (49)](https://github.com/chetp100/VSDSOC/assets/169384940/35796178-4095-4865-971c-0af427972dd1)

![Screenshot (50)](https://github.com/chetp100/VSDSOC/assets/169384940/38f5a987-9870-43ed-b089-8f51ead5a3dc)



Final step is Routing

```
run_routing

```

using magic file in result/routing of runs folder we can see routing

![Screenshot (51)](https://github.com/chetp100/VSDSOC/assets/169384940/25aa3ff4-cf10-4eff-948c-49b83815991d)

![Screenshot (52)](https://github.com/chetp100/VSDSOC/assets/169384940/31efaf3e-b800-444e-8aa3-27ba389ce8d0)


































































































