#MAE148 Fall 2025 - Team 9 - Smart Parallel Parking Robot
MAE148 Fall 2025 - Team 9 - Smart Parallel Parking Robot created by GitHub Classroom
# Parallel Parking Car with Sign Identification and Obstacle Remover

### Team Members
* **Trew Hoffman** - Mechanical Engineering: Software - Class of 2026
* **Manan Tuteja** - Aerospace Engineering: Hardware - Class of 2026
* **Terri Tai** - Computer Engineering - Class of 2025
* **Owen Hanenian** - Mechanical Engineering: Hardware - Class of 2026

---

## Overview
This project implements an autonomous parallel-parking robot that identifies which of two parallel parking spots is available and executes a full parking maneuver accordingly. The robot uses a vision-based decision pipeline, detecting no-parking signs, measuring depth to an AprilTag, and chooses the correct side to park.

The full system runs on ROS2, uses an OAK-D Lite for stereo depth + RGB vision, controls the car through a custom Hardware Abstraction Layer (HAL) connected to a VESC, and includes a servo-driven sweeper mechanism for obstacle removal.

The design intentionally follows a “Look → Measure → Execute” architecture, ensuring that every parking action is informed by sensor data.

## Abstract
Our goal was to create an autonomous ground robot that travels along a straight hallway with two potential parking spaces—one on the left and one on the right. A red NO PARKING sign declares one spot as occupied, and the robot must determine which side is open, measure its distance to the AprilTag marking the correct parking spot, and perform a tight parallel-parking sequence.

The system relies on the OAK-D Lite’s depth and rectified stereo output to estimate the true distance to an AprilTag using a median-over-area approach. The RGB stream is used to detect large red circular regions (NO PARKING signs) or, in ambiguous cases, a left-versus-right red-pixel imbalance.

Once the spot is selected, the orchestrator executes a multi-step parking routine using the HAL, steering, reversing, and straightening until the robot is aligned within its chosen spot. A sweeper arm powered by a servo motor controlled via a PCA9685 removes debris blocking the parking path.

## Key Features
* **Vision-based sign detection:** Identifies red circular no-parking signs or left/right red distribution imbalance to determine which spot is closed via HSV mask. 
* **AprilTag depth measurement:** [Computes tag distance using OAK-D rectified stereo depth, median-filtered for accuracy.
* **Feature 3:** [Brief description]

## Core Objectives
* **Objective A:** [e.g., Implement a tracking node...]
    * *Measure:* [How do you quantify success?]
    * *Action:* [What does the system do with this data?]
* **Objective B:** [e.g., Robot remains stationary until...]

## 4. System Architecture
### Node Descriptions
* **`[node_name].py`**
    * **Inputs:** [e.g., Camera feed, Lidar scan]
    * **Logic:** [Briefly explain the processing]
    * **Outputs:** [e.g., Motor control commands]
* **`[node_name].py`**
    * **Inputs:** [...]
    * **Outputs:** [...]

## 5. Hardware & Embedded Systems
* **Compute Unit:** [e.g., Jetson Nano] running [OS].
* **Sensors:** [List sensors used].
* **Connectivity:** [e.g., Wireless SSH].
* **CAD/Mechanical:**
    * *Custom Parts:* [List parts you designed]
    * *Stock Parts:* [List standard components]

## 6. Setup & Execution
1. **Environment:** `[command to source environment]`
2. **Build:** `colcon build --packages-select [package_name]`
3. **Launch:** `ros2 launch [package_name] [launch_file.py]`

## 7. Future Improvements
* [Improvement 1]
* [Improvement 2]

## 8. Acknowledgments
* [Credit professors, TAs, or open-source libraries]
