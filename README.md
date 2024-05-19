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











































