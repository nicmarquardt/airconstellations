# AirConstellations Project (UIST 2021)

This repository provides STL files for 3D-printing the sensor cases, enclosures, and other attachments for building an AirConstellations armature. Please refer to our paper for more details about the technical setup of our hardware.


![Visual overview of the AirConstellations project](https://github.com/nicmarquardt/airconstellations/blob/main/Figures/Overview.png?raw=true)

### AirConstellations: In-Air Device Formations for Cross-Device Interaction via Multiple Spatially-Aware Armatures
Publication at UIST 2021 – ACM Symposium on User Interface Software and Technology.

_Project by Nicolai Marquardt, Nathalie Henry Riche, Christian Holz, Hugo Romat, Michel Pahud, Frederik Brudy, David Ledo, Chunjong Park, Molly Jane Nicholas, Teddy Seyed, Eyal Ofek, Bongshin Lee, William A.S. Buxton, Ken Hinckley_

(Microsoft Research, University College London, ETH Zurich, Autodesk Research, University of Washington, UC Berkeley)

**Abstract:** AirConstellations supports a unique semi-fixed style of cross-device interactions via multiple self-spatially-aware armatures to which users can easily attach (or detach) tablets and other devices. In particular, AirConstellations affords highly flexible and dynamic device formations where the users can bring multiple devices together in-air – with 2-5 armatures poseable in 7DoF within the same workspace – to suit the demands of their current task, social situation, app scenario, or mobility needs. This affords an interaction metaphor where relative orientation, proximity, attaching (or detaching) devices, and continuous movement into and out of ad-hoc ensembles can drive context-sensitive interactions. Yet all devices remain self-stable in useful configurations even when released in mid-air. We explore flexible physical arrangement, feedforward of transition options, and layering of devices in-air across a variety of multi-device app scenarios. These include video conferencing with flexible arrangement of the person-space of multiple remote participants around a shared task-space, layered and tiled device formations with overview+detail and shared-to-personal transitions, and flexible composition of UI panels and tool palettes across devices for productivity applications. A preliminary interview study highlights user reactions to AirConstellations, such as for minimally disruptive device formations, easier physical transitions, and balancing "seeing and being seen" in remote work.

### Hardware setup
We retrofit these off-the-shelf armatures with sensors to continuously track the position and orientation of each device. The technical setup of a single AirConstellations arm is illustrated in the figure below.
In each AirConstellations arm we use an Arduino MKR 1010 Wifi (SAMD21 Cortex-M0+) microcontroller, with a 1-to-8 I2C multiplexer (TCA9548A), connecting to four IMUs (Inertial Measurement Units), all either MPU6050 or MPU9250. We use one IMU for each of the two main joints of the arm, one for the base (so we can sense the placement of the base) and the other for the joint that connects to the tablet at the end of the mount. To eliminate yaw-axis drift (a challenge with most IMU-based sensing), we do not use any yaw-axis measurement from the IMUs but added mechanical rotation sensors. We use high-precision 10-turn rotation sensors (Bourns 3510) with a connected 1:5 gear translation in the base, and an additional rotation sensor connected to the top joint where the device gets connected. Our algorithm then combines the yaw-axis rotation measures (from the base and head rotation axis) with the pitch-axis measures provided by the IMUs for determining the 3DoF position of the device in space, together with 3DoF orientation of the device around the head of the mounting arm. Using off-the-shelf armature mounts and low-cost sensing hardware makes this approach scalable and easy to replicate. In this Github repository we release the STL designs for the 3D-printed sensor enclosures, attachments, and other fixtures.

![Hardware setup](https://github.com/nicmarquardt/airconstellations/blob/main/Figures/Hardware.png?raw=true)

To better understand the parameters for creating dynamic in-air device formations, we synthesized a design space along dimensions that represent varying interaction techniques, sensing fidelity, physical characteristics, and spatial arrangements: 

![Design space](https://github.com/nicmarquardt/airconstellations/blob/main/Figures/Designspace.png?raw=true)
