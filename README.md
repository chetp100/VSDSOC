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




















