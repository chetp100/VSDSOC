# VSD SoC design Program
# Contents
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
















































































