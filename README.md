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







