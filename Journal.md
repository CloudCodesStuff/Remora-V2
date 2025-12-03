# Designing REMORA: My First PCB from Scratch!

REMORA as in the fish that sticks to the bottom of sharks:  
![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTY1MDQsInB1ciI6ImJsb2JfaWQifX0=--3eb5c4a6c1066cc825c04318a98d47e5139ca84f/image.png)

I decided to use the Seeed XIAO ESP32-C3 as the brain because it's small and has Wi-Fi. I needed a way to connect it to an MPU6050 sensor, battery, and LED without messy wires and I'm also aiming for tier 3, so I chose to design a custom "carrier board" in EasyEDA.

After asking on Reddit, my first attempt at the schematic was messy. I decided to use netLabels. I also wired in a switch to turn it on and off, as well as a white LED.

![Screenshot 2025-11-29 224208](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTY1MDEsInB1ciI6ImJsb2JfaWQifX0=--596de48b11f38cbe7b7a863af5ac845f878e0a3e/Screenshot%202025-11-29%20224208.png)

As you can see, it's very messy, and the wires around the sensor make it look like it's being shorted.

I cleaned it up, resulting in this:  
![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTY1MDIsInB1ciI6ImJsb2JfaWQifX0=--8162aea49768999cfc406910fcb08cc53249db67/image.png)

After that, I moved on to the PCB layout, where I ended up with this:

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTY1MDMsInB1ciI6ImJsb2JfaWQifX0=--191e45ad4eb988b1bab945ba39e4b4a10b76d6c6/image.png)

This could definitely be shrunken down, but I like the RPI Zero form factor so I went with these dimensions.

Overall a really productive Saturday for this. I'm going to work on the CAD today, and ensure all the parts for the PCB are good to go.

# Fixed some PCB issues (May have to search for new parts)

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTY3MTcsInB1ciI6ImJsb2JfaWQifX0=--37b6d943055410a68f44c0e8b2c687fb36772806/image.png)

Added some 3D models for what I could on EasyEDA. Moved the resistor over and changed the footprint to work on JLCPCB. I also found out that the switch I was going to buy takes way too long to arrive in the US. I'll have to find an alternative that will arrive before December 5th.

The BOM is also coming along nicely. Right now I'm at $68.29, and I'm looking to cut it down a little more.

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTY3MjAsInB1ciI6ImJsb2JfaWQifX0=--363974e115d1415d86e2f6717f35405fc353a6ac/image.png)

After looking through some battery options, I also may use a JST connector rather than a screw terminal. A drawback is that I can only use LiPos with JST connectors, and if the connector on the battery were to break, I would be stuck.

# Moved to ESP32 S3 Wroom, with simple devboard

![Schematic_remora-V3_2025-12-02](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTcxMTYsInB1ciI6ImJsb2JfaWQifX0=--9be4d15747858c5a6c8762f6ca9a78af7061fa3a/Schematic_remora-V3_2025-12-02.png)

This is an amalgamation of several schematics tutorials. I added in the GY521 board, and put it onto two unused GPIO pins. In code I will set it because the S3 allows you to modify pins like that. I would have loved to add the actual MPU6050 onto the PCB rather than a breakout board, but that's beyond my scope and time before Friday.

Tomorrow I will be working on the PCB layout, then the BOM.

# Finished the PCB Layout and routing, and fixed errors

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTcyNDgsInB1ciI6ImJsb2JfaWQifX0=--581f58550e088a4d2c2d7cbd1b4729dc69d9eb69/image.png)

Put everything on the PCB on my own. The GY521 module takes up a huge amount of space. If I could move the components from that module onto the board, it would save a lot of room, but that is not possible on this timeline.

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTcyNDksInB1ciI6ImJsb2JfaWQifX0=--7a7cb7ae7d4277f4040354a27782769de96662e1/image.png)

3D model above.

# CAD COMPLETE

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTczMzksInB1ciI6ImJsb2JfaWQifX0=--780c7f70d420117e0d12d3469174b6d177f91cda/image.png)

I finished up the case design and added two rectangular channels along the bottom. These hold the ESP32 S3 PCB in place by gripping the outer edges of the header pins.

I relocated the JST battery connector to the bottom edge of the PCB so the LiPo can slide underneath the board once installed, which keeps the design compact.

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTczNDQsInB1ciI6ImJsb2JfaWQifX0=--8f9d6fb1bef44f95769f00857cda6581eb3e58fa/image.png)

I included vents based on a design I found online, though the ESP32 likely will not run hot.

# Finalizing end pricing

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTc0NjMsInB1ciI6ImJsb2JfaWQifX0=--8d85bc39ec2b1343792a1601303d4bf00be2a5ac/image.png)

With the standard components, price on PCBA would have been extremely high (around 120), so I decided I will solder the ESP on myself, along with an RGB LED and the headers.

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTc0ODUsInB1ciI6ImJsb2JfaWQifX0=--bd89f5e88da0a3913b786e5bbd28663ce079bf0a/image.png)

LCSC cart for LED and ESP.

I will be putting together the GitHub shortly with all relevant files.
