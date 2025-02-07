# SDR-Based-RF-Signal-Analysis-and-Replay-Attack
![Status](https://img.shields.io/badge/Status-Completed-green)
![Tech](https://img.shields.io/badge/Tools-SDR%2CGNU%20Radio%2C%20Inspectrum%2C%20Python%20-%20blue)

## 📌 Overview 
This repository contains my project on **Software-Defined Radio (SDR)** technology, focusing on RF signal analysis, digital modulation techniques, and security implications of wireless systems. The project demonstrates:
- RF signal capture and analysis
- Implementation of a replay attack on a wireless doorbell
- Generation of RF packets from scratch
- Decoding of hidden messages in RF transmissions

This project showcases practical skills in SDR technology and wireless security.

---

## 📖 Table of Contents
- [Key Topics Covered](#key-topics-covered)  
- [Files Included](#files-included)  
- [Tools & Technologies Used](#tools--technologies-used)  
- [Methodology](#methodology)  
  - [Environment Setup](#0️⃣-environment-setup)  
  - [SDR Setup](#1️⃣-sdr-setup)  
  - [Running GNU Radio and setting up the flowgraph](#2️⃣-running-gnu-radio-and-setting-up-the-flowgraph)  
  - [Replay Attack](#3️⃣-replay-attack)    
- [Ethical Considerations](#ethical-considerations)  
- [Learning Outcomes](#learning-outcomes)  
- [Contact](#contact)  
- [Acknowledgements](#acknowledgements)

---

## Key Topics Covered 
- **RF Signal Capture:** Using SDR (PlutoSDR/LimeSDR) for precise signal acquisition
- **Signal Analysis:** Utilizing GNU Radio and Inspectrum for comprehensive analysis
- **Replay Attack:** Demonstrating vulnerabilities in a wireless doorbell system
- **Packet Generation:** Creating RF packets from decoded data
- **Message Decryption:** Techniques for uncovering hidden information in RF signals

---

## Files Included  
| File Name | Description |  
|-----------|------------|  
| `screenshots/*` | All the screenshots to execute this attack |
| `flowgraphs/fm_receive.grc` | GNU receiver flow graph|
| `flowgraphs/fm_transmit.grc` | GNU transmitter flow graph|


---

## Tools & Technologies Used  
- **Software-Defined Radio (SDR) Hardware**  
- **GNU Radio Companion** - Creating Transmitter & Receiver for S
- **Inspectrum** – Signal Analysis  
- **Python** – Scripting for automated attacks

---

## Methodology

### 0️⃣ Environment Setup

```bash
sudo apt install gnuradio
sudo apt install inspectrum
```

```bash
#libiio dependencies
sudo apt-get update
sudo apt-get install build-essential cmake libxml2-dev libusb-1.0-0-dev libserialport-dev libavahi-client-dev libzstd-dev
git clone https://github.com/analogdevicesinc/libiio.git
cd libiio
mkdir build && cd build
cmake ../ -DCPP_BINDINGS=ON -DPYTHON_BINDINGS=ON
make -j$(nproc)
sudo make install
```

```bash
# gr-iio dependencies
git clone https://github.com/analogdevicesinc/gr-iio.git
cd gr-iio
mkdir build && cd build
cmake ..
make
sudo make install
sudo ldconfig
```

### 1️⃣ SDR Setup
- Connect the SDR device to the computer
```bash
ssh root@192 .168.2.1 # password = analog
```
```bash
fw_setenv attr_name compatible
fw_setenv attr_val ad9364
reboot
fw_setenv compatible ad9364
reboot
```

### 2️⃣ Running GNU Radio and setting up the flowgraph
```bash
gnuradio-companion
```
- Use the transmitter and receiver flowgraphs provided in the repository.
- Play around with the values in the graph until you get a clear signal.
- The captures can be analysed in Inspectrum.

### 3️⃣ Replay Attack
- Use Inspectrum to find the peaks in the signal.
- Use the transmitter flowgraph to replay the signal.
- This atack was executed on a doorbell and it successfully replayed the signal and the doorbell rang.
- The signal can also be generated from scratch by analysing the captured signal. This can be done using vector source block in gnu radio.

---

## Ethical Considerations
This project is for educational and research purposes only. Always obtain proper authorization before conducting security research on wireless systems.

---

## Learning Outcomes
- Gained practical experience in SDR hardware and software integration
- Developed proficiency in GNU Radio Companion for signal processing applications
- Enhanced understanding of digital modulation techniques and their implementations
- Acquired skills in wireless protocol analysis and reverse engineering
- Improved problem-solving abilities in real-world RF communication scenarios
- Developed a deeper understanding of wireless security vulnerabilities and countermeasures

---

## Contact
For any inquiries, feel free to reach out via:
📌 LinkedIn: www.linkedin.com/in/pranavs07

---

## Acknowledgements
This project was completed under the supervision of Dr. Aanjhan Ranganathan.
