+++
date = 2018-09-03T22:50:00
title = "Electric Keyboard"
summary = "An electric keyboard constructed out of an FPGA, a monitor, and 13 sensing circuits and custom-made keys."
image_preview = "keyboard.jpg"
tags = ["assembly", "fpga", "hardware", "software", "verilog"]
external_link = ""
math = false

# Optional featured image (relative to `static/img/` folder).
[header]
image = "headers/keyboard.jpg"
caption = "The electric keyboard itself."
+++

For my final project for my Digital Systems (ECE350) class, my friend and I created an electric keyboard that had both physical and digital components. We designed the piano keys themselves using [SketchUp](https://www.sketchup.com/) and 3D printed them.

![image](/~amanocha/img/model.png#center) <center>*Our SketchUp Model*</center>

Underneath the keys lay a breadboard that contained 13 identical sensing circuits, where each circuit was made up of resistors, a photoresistor, a transistor, and a light-emitting diode (LED):

![image](/~amanocha/img/lightsensor.png#center) <center>*Sensing Circuit Schematic*</center>

A piano key press was simulated by hovering (or touching) a finger over the edge of the key, where the photoresistor was located. We used an IRLD014 NPN MOSFET as a transistor to control when current should flow from its drain to its source, or from the 1K resistor to ground. The photoresistor was connected to the gate of the MOSFET as well as to a 10K resistor that was grounded. When the photoresistor was covered (received less light), its resistance decreased, so there was a lower voltage drop across it (less of a drop from VCC), which caused the gate voltage to increase. As the gate voltage increased, more current flowed from the drain of the MOSFET to the source and since the IR LED was connected to the drain of the MOSFET, more current flowed from VCC (3 volts) through the 1K resistor and into the LED (labeled "TO_DI" or "to diode"). Therefore, covering the photoresistor illuminated the LED and we were able to simulate a key lighting up by hovering a finger over the key.
