# Tiny, yet powerful

The PCB for this project is just **66*59.5mm**, which is not exactly tiny, but still has features that go beyond it's  size. It packs a STM32F407, debugger (STM32F103), Ethernet, a powerful motor driver, 24-bit ADC configured for a 4 - wire Kelvin load, DAC and mic into this tiny footprint.

# Why did I build this?

I had designed general dev boards for the ESP32, or the RP2040, but never worked with the STM32 family before. And I also wanted to make a really complex PCB to brush up my skills, so I decided on this.

# Double-sided component placement

While I was designing this PCB, I realised that in real-life applications, size is a key deciding factor; something I had never taken very seriously. So, I challenged to make this board under 70*70mm this time. Due to which, I had to place **components on both sides**. Not only does it make the PCB smaller, but also improves SI and clears up board space.

# 4-layer design

A 2-layer design was clearly not an option here. I both analog and digital circuitry here, requiring clear return paths. So, I decided on a 4 layer board with a GND and power plane. The power plane is sectioned into 12V and 3V3 volts. I did this because while most of the PCB needed 3.3V, the motor driver required +12V with minimal voltage drops and maximum current. But when only a few tracks were left, I couldn't find space on the outer two signal layers. I only had two options from there; either upgrade to a 6 layer board (expensive and really time consuming), or use a power plane for a few signals. I thought it might ruin the return paths for sensitive signals, so I googled for guides on that topic. After going through the ["Should You Route Signals in Your PCB Power Plane?" by Altium Academy](https://resources.altium.com/p/should-you-route-signals-your-pcb-power-plane), I decided to use the Vcc power plane for routing leftover signals.

# GPIO headers

To keep the form factor of the PCB low and keep things organised, I didn't breakout GPIO headers. Although this limits the capabilities of the controller to the existing peripherals only, I still went with it as the whole idea of this project was to design a compact, complex PCB for learning new things. To expand the functionality a bit, I exposed two headers for UART and CAN.
# Motor drivers

In the beginning, I planned on two motor drivers, as in the Block Diagram and Power budget. But while designing the schematic, I thought that a single driver was enough and didn't design the second. But to keep things upgradeable, I still kept it in the Power budget and block diagram

# Power Supply

The board requires **+12v, +3V3 and +1V8** to work. For that, I use a 3-pin 10A TBC for inputting 12V, and regulating it down to +3V3 and +1V8. As calculated in the power budget, I need a power supply capable of delivering roughly 10A, though with the second motor removed, a 7.5A supply may also be used.

# How to use it?

1) Solder your PCB
2) Use an **ST-Link debugger (recommended)/USB to UARTconverter** to flash the [**DAPLink firmware by ARMbed**](https://github.com/ARMmbed/DAPLink) onto the STM32F103
3) Plug it in, and you're ready to go!

# Block Diagram

<img width="1223" height="867" alt="image" src="https://github.com/user-attachments/assets/4ff0f524-eda2-43c6-9211-8026f32be982" />

# PCB

<img width="650" height="624" alt="image" src="https://github.com/user-attachments/assets/20cd1878-ab3c-4bff-8e33-a931081c5ed7" />

# 3D view (front)

<img width="980" height="854" alt="image" src="https://github.com/user-attachments/assets/8fa3ac39-02ce-4099-82ec-1d295531def8" />

# 3D view (back)

<img width="943" height="845" alt="image" src="https://github.com/user-attachments/assets/8355902d-b20d-4318-889f-481a3bb0c848" />

