# Network Controlled LED System

# Overview
This project aims to establish a network-based control system for the LEDs on a DE1-SoC board. It leverages the functionalities of both the built-in Field Programmable Gate Array (FPGA) and the ARM processor (HPS) on the DE1-SoC. This project demonstrates a fundamental concept in computer networks, remote device control. It showcases how network communication protocols and hardware components can work together to achieve a specific action. The project highlights real-world applications like Networked Automation Systems, where similar principles are used in industrial settings where machines or devices are controlled remotely via network commands. This project combines software and hardware to achieve remote control functionalities of LEDs on the DE1-SoC board, providing hands-on experience with network programming, hardware-software integration, and practical applications of these concepts.

# Introduction
The DE1-SoC board, developed by Terasic, integrates an Altera Cyclone V FPGA and a dual-core ARM Cortex-A9 processor, making it a versatile platform for a wide range of applications, from embedded systems to advanced computing tasks. In this project, the DE1-SoC board is used to demonstrate the control of onboard LEDs through network commands sent over TCP/IP.

Remote control systems are crucial in various industrial and automation applications. This project explores the implementation of a network-based control system for LEDs on the DE1-SoC board, showcasing the practical application of network communication for remotely controlling hardware devices. By sending commands from a client computer to the DE1-SoC board, we can toggle the state of the LEDs, providing a clear example of remote hardware control. 

# Design 
The network-controlled LED system utilizes a client-server architecture for communication. The system architecture includes:

- Client Application: This application, running on a separate computer, allows users to send control commands for the LEDs. It establishes a TCP/IP connection with the server program on the DE1-SoC board, transmits commands over the network, and receives confirmation messages from the server when a command is accepted.

- HPS Server Program: This program runs on the DE1-SoC’s ARM processor, it acts as the server. It listens for incoming connections on a specific port, parses received commands from the client and interacts with the FPGA logic to control the LEDs. The server program also sends confirmation messages back to the client for successful command execution.

The block diagram below shows how commands sent over the network from the computer are received by the server program on the HPS. The program parses the commands and sends control signals to the FPGA logic, which activates or deactivates LEDs on the board.  

<p align="center">
  <img src="https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/d2b4b72c-374f-4f69-957b-1ab3f59e15fc" alt="High Level Design">
</p>
<p align="center">
  Figure 1. High Level Design
</p>

The system leverages the TCP/IP protocol suite for reliable network communication. TCP, Transmission Control Protocol, establishes a connection between the client and server, ensuring data arrives in the correct order and without errors. Here is a simple breakdown of the TCP communication flow:

- Connection Establishment: The client initiates a connection request to the server on a specific TCP port. The server acknowledges the request, and a connection is established.

- Data Transfer: The client sends control commands as data packets over the established connection. The server receives these packets and acknowledges their receipt.

- Connection Termination: Once communication is complete, the client and the server initiate a connection termination sequence, closing the connection.

<p align="center">
  <img src="https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/fa695163-6649-4d27-be10-44dfa672e6ec" alt="Network Communication Flow">
</p>
<p align="center">
  Figure 2. Network Communication Flow
</p>

In this diagram we see, the client sends commands to the server using TCP and the server processes these commands and sends back a confirmation to the client.

# Implementation 
To get the server program onto the DE1-SoC I had to connect the SoC board to my home router. By doing this it connected the board to my LAN (Local Area Network). Once connected to the LAN, I used Secure Copy Protocol (SCP) to transfer the server program from my desktop computer to the board. SCP is a network protocol that allows file transfer between hosts on a network. It is based on the Secure Shell (SSH) protocol, which allows for the operation of network services over an insecure network. OpenSSH developers recommend using more modern protocols like SFTP (Secure File Transfer Protocol) however, for our problem SCP works.

<p align="center">
  <img src="https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/85c64951-2a4f-4b4b-a1de-b95cc39cac94" alt="SCP to De1SoC">
</p>
<p align="center">
  Figure 3. SCP to De1SoC
</p>

In Figure 3, we see SCP being used to transfer server.py over to the De1SoC. Now that sever.py is successfully transferred to the DE1SoC we can host the server on the board. 
Now, we can connect to the server on any device on the network using the Client.py file. The Client.py script allows users to establish a connection with the server running on the DE1-SoC board, send commands to control the LEDs remotely, and receive confirmation from the server about the status of the commands sent.

<p align="center">
  <img src="https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/c78a42fc-fe66-4a27-9c4d-8e626ba68765" alt="Client-Sever Interaction">
</p>
<p align="center">
  Figure 4. Client-Sever Interaction
</p>

In Figure 4, we see the client and server interacting with each other. We see the established TCP connection where the client initiates a connection request to the server on a specific TCP port. The server acknowledges the request, and a connection is established.  The client then sends control commands as data packets over the established connection. The server receives these packets and acknowledges their receipt. Once communication is complete, the client and the server initiate a connection termination sequence, closing the connection.

Figure 4 shows us the client sending the command 1 and 3 which turns LED1 and LED3 on the DE1-SoC. Below is the result of these commands on the board. 

<p align="center">
  <img src="https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/6147dc73-3555-441f-9d9d-bf2c58ece583" alt="De1-SoC Results">
</p>
<p align="center">
  Figure 5. De1-SoC Results
</p>

Figure 5 shows us the results on the board. We see that once receiving the commands from the client, the server correctly tells the board to turn LED1 and LED3 on. Through this implementation, the project successfully demonstrates the remote control of hardware components via network commands, providing hands-on experience with network programming, hardware-software integration, and the practical application of these concepts in real-world scenarios.

# Conclusion
This project successfully demonstrated the implementation of a network-controlled LED system using the DE1-SoC board, showcasing the integration of network communication protocols with hardware control. By leveraging both the FPGA and ARM processor on the DE1-SoC, we achieved a seamless client-server interaction that allowed remote control of the board's LEDs via TCP/IP commands. Overall, the project illustrates the potential of network-based control systems in industrial and automation applications, where remote device control is critical. The successful execution of this project underscores the importance of combining theoretical knowledge with practical implementation to solve real-world engineering challenges.

# Demonstration 

https://github.com/JuanCantu1/Network-Controlled-LED-System/assets/109363196/245d2584-dca9-4737-8c14-c83175a772fb
