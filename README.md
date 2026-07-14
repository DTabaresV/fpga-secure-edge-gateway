FPGA Secure Edge Gateway for IoT/5G  
DE10-Nano SoC · USB Camera · FPGA Video Pipeline · Nginx HTTPS Server · Java JAX‑RS Web Application · Secure Remote Access

This project implements a secure FPGA-based edge gateway using the **DE10-Nano (Cyclone V SoC)**.  
It captures video from a USB UVC camera on the HPS, processes frames on the FPGA fabric, streams the processed video through an HTTPS-enabled Nginx server, and exposes a custom Java JAX‑RS web application accessible from any remote client.





**FPGA Processing**
- Color-space conversion (RGB/YUV)
- Basic video filtering pipeline
- Hardware hashing (SHA-256) for frame integrity
- Control registers accessible from HPS

**HPS (Armstrong Linux)**
- USB UVC camera capture
- DMA transfer of frames to FPGA
- MJPEG streaming service
- Nginx reverse proxy with **HTTPS/TLS**

**Java Web Application (JAX‑RS)**
- Custom REST API using **javax.ws.rs / Jersey**
- HTML viewer served through JAX‑RS resources
- Live video stream embedded in the web interface
- Token-based authentication

**Security**
- HTTPS/TLS encryption via Nginx
- Token-based access control
- Hardware hashing for integrity


---

**System Architecture**

USB Camera 
↓
HPS – Armstrong Linux
- Frame capture 
- DMA → FPGA
↓
FPGA Fabric
- Color-space conversion
- Filter pipeline
- Hashing core
↓
HPS
- MJPEG/H.264 streaming
- Nginx HTTPS reverse proxy
- Java JAX‑RS web application
↓
Client Browser
- HTTPS + token
- Live video stream



 **Repository Structure**

fpga-secure-edge-gateway/
├─ docs/
│  ├─ 00_overview.md
│  ├─ 01_armstrong_setup.md
│  ├─ 02_hps_usb_capture.md
│  ├─ 03_fpga_pipeline.md
│  ├─ 04_security_hashing.md
│  ├─ 05_streaming_nginx_https.md
│  ├─ 06_java_jaxrs_webapp.md
│
├─ hps/
│  ├─ capture_usb_uvc.c
│  ├─ dma_to_fpga.c
│  ├─ stream_mjpeg.sh
│  ├─ nginx.conf
│  ├─ certs/ (TLS certificates)
│
├─ fpga/
│  ├─ rtl/
│  │  ├─ color_space_conv.v
│  │  ├─ filter_pipeline.v
│  │  ├─ hash_core.v
│  │  ├─ control_regs.v
│
├─ webapp/
│  ├─ src/
│  │  ├─ main/java/com/gateway/api/
│  │  ├─ main/resources/
│  ├─ pom.xml
