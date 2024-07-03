# Network Controlled LED System

# Overview
This project aims to establish a network-based control system for the LEDs on a DE1-SoC board. It leverages the functionalities of both the built-in Field Programmable Gate Array (FPGA) and the ARM processor (HPS) on the DE1-SoC. This project demonstrates a fundamental concept in computer networks, remote device control. It showcases how network communication protocols and hardware components can work together to achieve a specific action. The project highlights real-world applications like Networked Automation Systems. Similar principles are used in industrial settings where machines or devices are controlled remotely via network commands. This project will combine software and hardware to achieve remote control functionalities of LEDs on the DE1-SoC board. At the end I will have gained hands-on experience with network programming, FPGA design, and integration of hardware and software components for network-based control systems. 

# Introduction
The DE1-SoC board, developed by Terasic, integrates an Altera Cyclone V FPGA and a dual-core ARM Cortex-A9 processor, making it a versatile platform for a wide range of applications, from embedded systems to advanced computing tasks. In this project, the DE1-SoC board is used to demonstrate the control of onboard LEDs through network commands sent over TCP/IP.

Remote control systems are crucial in various industrial and automation applications. This project explores the implementation of a network-based control system for LEDs on the DE1-SoC board, showcasing the practical application of network communication for remotely controlling hardware devices. By sending commands from a client computer to the DE1-SoC board, we can toggle the state of the LEDs, providing a clear example of remote hardware control. 

# Design 
The network-controlled LED system utilizes a client-server architecture for communication. The system architecture includes:

-	Client Application: This application, running on a separate computer, allows users to send control commands for the LEDs. It establishes a TCP/IP connection with the server program on the DE1-SoC board, transmits commands over the network, and receives confirmation messages from server when a command is accepted.

-	HPS Server Program: This program runs on the ARM processor core of the DE1-SoC acts as the server. It listens for incoming connections on a specific port, parses received commands from the client, and interacts with the FPGA logic to control the LEDs. The server program also sends confirmation messages back to the client for successful command execution.

The diagram below shows how commands sent over the network from the computer are received by the server program on the HPS. The program parses the commands and sends control signals to the FPGA logic, which activates or deactivates LEDs on the board. 

![image](https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/d2b4b72c-374f-4f69-957b-1ab3f59e15fc)

The system leverages the TCP/IP protocol suite for reliable network communication. TCP, Transmission Control Protocol, establishes a connection between the client and server, ensuring data arrives in the correct order and without errors. Here is a simple breakdown of the TCP communication flow:

-	Connection Establishment: The client initiates a connection request to the server on a specific TCP port. The server acknowledges the request, and a connection is established.

-	Data Transfer: The client sends control commands as data packets over the established connection. The server receives these packets and acknowledges their receipt.

-	Connection Termination: Once communication is complete, the client and the server initiate a connection termination sequence, closing the connection.

  ![image](https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/fa695163-6649-4d27-be10-44dfa672e6ec)

In this diagram we see, the client sends commands to the server using TCP and the server processes these commands and sends back a confirmation to the client.

# Implementation 
This section will show The implementation of the system.

# Demonstation 

https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/245d2584-dca9-4737-8c14-c83175a772fb

