---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Let's embark on an exciting journey into FPGA programming as I turn hardware concepts into vibrant visuals. 

## **Template VGA Design**
### **Project Set-Up**
For this project, I used an FPGA board, the Basys3 paired with Verilog code to implement the VGA design. I setup the project using Vivado, a powerful software tool used for designing and programming FPGA-design system. While setting up, I specified the board and included all the design files. The siles include the VGTop.v, ColorStripes.v, ColorCycle.v and VGASync. These were the design files, with the VGA sync being the simulation file.

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-03%20131912.png">

### **Template Code**
The provided Verilog templates show the basiscs of VGA interface. They show appropriate timing signals (HSYNC and VSYNC) and pixel data to drive a display. VGA operates by sending pixel data line-by-line in sync with timing signals, maintaining a precise refresh rate.

The code is modular, with clear distinctions between the timing generator and pixel data modules. For example:

The Timing Generator ensures proper synchronization.
The Color Module determines the visual output per pixel.
### **Simulation**
The simulation process helps us to see how the design works, it shows the signals in waveforms and how they vary in real time. Initially when the project is set-up the simulation file (VGASync.v) is at the top of the hierarchy, so it is important to move the to the simulation source so that simulation can be performed. 
In the simulation: 
- The clck signal toggles consistently, driving the timing logic of the VGA system.
- col increments sequentially as part of the horizontal pixel counting.
- When col resets to zero, row increments, indicating a transition to the next line.
- As for the RGB signals, each color is repesented by 4 bits.
- 
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
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

This piece of code was essential for the State machine and I adapted it from the colour cycle code. At the end of each state, the condition will allow the state machine to go to the next state.

<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-10%20155339.png">

### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs. 
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

