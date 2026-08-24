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


## Basic CORDIC Functioning

CORDIC is an iterative algorithm used to calculate mathematical functions using:

- Addition
- Subtraction
- Bit shifting

This makes it highly suitable for FPGA implementation because complex multiplication and division operations can be avoided.

In this project, CORDIC operates in **Vectoring Mode**. The input vector is gradually rotated towards the x-axis until the y-component approaches zero.

For each iteration, the rotation angle is:

$$
\theta_i = \tan^{-1}(2^{-i})
$$

The CORDIC iterative equations are:

$$
x_{i+1} = x_i - d_i y_i 2^{-i}
$$

$$
y_{i+1} = y_i + d_i x_i 2^{-i}
$$

$$
z_{i+1} = z_i - d_i \tan^{-1}(2^{-i})
$$

where $d_i$ determines the direction of rotation.

After the required number of iterations:

$$
y_n \approx 0
$$

The final values are then used to calculate the magnitude and angle of the input vector.
