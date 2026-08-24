## Overview

This project implements the **CORDIC (COordinate Rotation DIgital Computer)** algorithm for calculating the **distance (magnitude)** and **angle** of a two-dimensional vector.

The CORDIC hardware was implemented on the **PYNQ-Z2 FPGA development board**. Given the Cartesian coordinates:

$$
(x,y)
$$

the algorithm calculates:

- **Distance (Magnitude)**
- **Angle**

A **MicroBlaze soft processor** was used to interface with the CORDIC hardware. The software application was developed using **Xilinx Vitis**, and the calculated distance and angle were displayed on a serial terminal through a **UART interface using the Real Digital Boolean Board**.

---

## Basic CORDIC Functioning

CORDIC is an iterative algorithm used to calculate mathematical functions using simple operations such as:

- Addition
- Subtraction
- Bit shifting

This makes it highly suitable for FPGA implementation, as complex multiplication and division operations can be avoided.

In this project, CORDIC operates in **Vectoring Mode**. The input vector is iteratively rotated towards the x-axis until its y-component approaches zero.

For each iteration, the predefined rotation angle is:

$$
\theta_i = \tan^{-1}(2^{-i})
$$

The CORDIC vectoring equations are:

$$
x_{i+1} = x_i - d_i y_i 2^{-i}
$$

$$
y_{i+1} = y_i + d_i x_i 2^{-i}
$$

$$
z_{i+1} = z_i - d_i \tan^{-1}(2^{-i})
$$

where $d_i$ determines the direction of rotation during each iteration.

After the required number of iterations:

$$
y_n \approx 0
$$

The final x-value is used to determine the magnitude of the input vector, while the accumulated angle $z_n$ represents the angle of the vector.
