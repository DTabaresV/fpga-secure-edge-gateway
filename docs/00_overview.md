# 00 – Project Overview

## 1. Purpose
This document describes the overall architecture and goals of the FPGA Secure Edge Gateway project.

## 2. System Architecture
Camera → HPS → FPGA → HPS → Nginx (HTTPS) → Java JAX-RS → Client.

## 3. Components
- DE10-Nano (Cyclone V SoC)
- Armstrong Linux
- USB UVC camera
- FPGA RTL modules
- Nginx HTTPS server
- Java JAX-RS web application

## 4. Data Flow
Describe how frames move from camera → HPS → FPGA → HPS → Nginx → Browser.

## 5. Security Model
Explain HTTPS, token authentication, hashing, and future PQC integration.

## 6. Repository Structure
Explain the folders and their purpose.

## 7. Roadmap
List milestones and future improvements.
