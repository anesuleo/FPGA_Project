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
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
As for my design, I decided to make a smiley face and then a cycle of 3 colours from left to right. This was a combination of the colour cycle and colour stripes templates. 
### **Code Adaptation**
I started working and making changes on the colour stripes, as initially I had no plan of adding the colour cycle at the end. To satrt of I had to draw a layout of what I wanted to visualise. I used pixel art [Pixil Art](https://www.pixilart.com/) to draw the picture, using a resolution of 64 by 48 which would help me translate the picture to code. 
<img src="https://github.com/anesuleo/FPGA_Project/blob/main/docs/assets/images/Screenshot%202024-12-03%20131912.png">
As for the colour rotation at the end, I used code from the colour cycle to write code for the state, machine.
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
