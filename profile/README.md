# Coda: A Digital Cockpit

## About Coda
Coda is a multi-ECU, AI-driven, state of the art well-rounded system featuring two screens, road sign detection, a voice assistant, and intuitive UI that elevates a driver's experience to a new level.


Coda represents the team's magnum opus: the graduation project of a long and hard journey in Information Technology Institute's 9 Month Professional Training Program Embedded Systems Track. You can consider it a love letter to this place; where all the skills acquired along the way have been put to the test. Our team is proud to say the output has been above our expectations.

## Under The Hood
Coda comprises of 4 main nodes:
1. Baremetal Node: responsible for direct hardware interfacing for determining doors states, car speed and rpm, and ultrasonic sensors for safe-distance. These readings are sent via CAN. This ECU is based on the NXP S32K148-Q176.
2. Detection Node: responsible for detecting road signs from a predefined selection while on the road. The detection model is a YOLOv8 nano model that was trained on a set of road signs. The detected signs are published to the Cluster Node via a CommonAPI service based on vSOME/IP. This ECU is based on NVIDIA Jetson Nano Developer's Kit running a custom Yocto distro. 
3. Cluster Node: responsible for running the Instrument Cluster app on the first screen and routing CAN traffic towards the IVI Node. The Instrument Cluster app is built using Qt6 framework. The app displays some of the incoming data from CAN and forwards the rest to the IVI Node via a CommonAPI service based on vSOME/IP. This ECU is based on Raspberry Pi 5 16GB running a custom Yocto distro. 
4. IVI Node: responsible for running the IVI app on the second screen in addition to a Voice Assistant app complying with Google's guidelines for development. The incoming data from Cluster Node is received via a CommonAPI service based on vSOME/IP; this service transfers the readings to the application layer through an AIDL contract that is used for registering callbacks in the application layer. Coda's Voice Assistant features wake word detection and multiply commands.

## Main Repositories
1. [IVI App](https://github.com/Coda-ITI/IVI-Coda)
2. [Instrument Cluster App](https://github.com/Coda-ITI/InstrumentCluster)
3. [Voice Assistant App](https://github.com/Coda-ITI/Coda_Assistant)
4. [Road Sign Detection Model](https://github.com/Coda-ITI/road-sign-detection-YOLO)
5. [Android Automotive Vendor Package](https://github.com/Coda-ITI/Coda)
6. [Custom Yocto Meta Layer](https://github.com/Coda-ITI/meta-coda)
7. [Baremetal Firmware](https://github.com/Coda-ITI/NXP-Baremetal)
8. [Barmetal PCB](https://github.com/Coda-ITI/NXP-Expansion-Board)

## Manifests
1. [Cluster Node](https://github.com/Coda-ITI/cluster_manifest)
2. [Detection Node](https://github.com/Coda-ITI/jetson_manifest)
3. [IVI Node](https://github.com/Coda-ITI/android_local_manifest)
