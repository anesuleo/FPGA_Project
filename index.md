---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Let's embark on an exciting journey into FPGA programming as I turn hardware concepts into vibrant visuals. 

## **Template VGA Design**
### **Project Set-Up**
For this project, I used an FPGA board, the Basys3 paired with Verilog code to implement the VGA design. I setup the project using Vivado, a powerful software tool used for designing and programming FPGA-design system. During the setup, I specified the board and included all the design files. The siles include the VGTop.v, ColorStripes.v, ColorCycle.v and VGASync. These were the design files, with the VGA sync being the simulation file.

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-03%20131912.png">

### **Template Code**
The provided Verilog templates show the basiscs of VGA interface. They show appropriate timing signals (HSYNC and VSYNC) and pixel data to drive a display. VGA operates by sending pixel data line-by-line in sync with timing signals, maintaining a precise refresh rate. This refresh can not be seen by human eye.
The timing generator increments horizontal and vertical counters, ensuring smooth lin by line updates on the screen.
### **Simulation**
The simulation process helps us to see how the design works, it shows the signals in waveforms and how they vary in real time. Initially when the project is set-up the simulation file (VGASync.v) is at the top of the hierarchy, so it is important to move the to the simulation source so that simulation can be performed. 
In the simulation: 
- The clck signal toggles consistently, driving the timing logic of the VGA system.
- col increments sequentially as part of the horizontal pixel counting.
- When col resets to zero, row increments, indicating a transition to the next line.
- As for the RGB signals, each color is repesented by 4 bits.
  
### **Synthesis**
Synthesis is an essential process that transforms the Verilog code into hardware logic for the FPGA board. After the synthesis is done, the implementation follows. 
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
As for my design, I decided to make a smiley face and then a cycle of 3 colours from left to right. This was a combination of the colour cycle and colour stripes templates. 
### **Code Adaptation**
I started working and making changes on the colour stripes, as initially I had no plan of adding the colour cycle at the end. To satrt of I had to draw a layout of what I wanted to visualise. I used [Pixil Art](https://www.pixilart.com/) to draw the picture, using a resolution of 64 by 48 which would help me translate the picture to code. 

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-03%20131912.png">

As for the colour rotation at the end, I used code from the colour cycle to write code for the state machine.

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-10%20155302.png">

I set boundary values for every part of the face using the coordinates from the pixel art. As for the state machine, I initialised the four states, one for the face and the other three for the colour rotation from left to right. To start off, I had to make sure the default backround colour was balck. The yellow colour is a mix of red and green, so to produce colour I set all the bits for red and green to 1. 

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-10%20155329.png">

This piece of code was essential for the state machine and I adapted it from the colour cycle code. At the end of each state, the condition will allow the state machine to go to the next state.

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-10%20155339.png">

### **Synthesis**
During synthesis, I noticed slight differences in resource utilization due to the added state machine and additional logic for pixel boundaries. The implementation results confirmed correct timing and logic for my custom design. 
### **Demonstration**

The 

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/IMG_7277.jpg"> 

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/IMG_7336.jpg"> 

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/IMG_7337.jpg"> 

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/IMG_7338.jpg"> 


