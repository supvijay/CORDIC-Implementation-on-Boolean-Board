## Overview

This project implements the **CORDIC (COordinate Rotation DIgital Computer)** algorithm on the **PYNQ-Z2 FPGA development board**.

The CORDIC algorithm is used to calculate:

- **Distance (Magnitude)**
- **Angle**

of a two-dimensional vector given its Cartesian coordinates:

\[
(x,y)
\]

The design uses a **MicroBlaze soft processor** to communicate with the CORDIC hardware. The software application was developed using **Xilinx Vitis**, and the calculated **distance and angle are displayed through UART**.
