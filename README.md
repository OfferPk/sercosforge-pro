# SercosForge Pro (v1.0.0)

### SERCOS III (IEC 61784-2 / IEC 61491\) Real-Time Motion Protocol Studio, MDT/AT Telegram Dissector, Isochronous Timing Calculator, & Ring Safety Auditor

[![Version](https://img.shields.io/badge/version-1.0.0-red.svg)](https://github.com/sercosforge/sercosforge-pro) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT) ![Standard](https://img.shields.io/badge/IEC%2061784--2-Compliant-green.svg) ![Standard](https://img.shields.io/badge/IEC%2061491-Compliant-green.svg) ![Tests](https://img.shields.io/badge/Tests-10%2F10%20Passing-brightgreen.svg)

---

## What is SercosForge Pro?

**SercosForge Pro** is an open-core, zero-dependency engineering suite designed for CNC machine builders, multi-axis motion control engineers, robotics developers, and industrial automation teams working with **SERCOS III (Serial Real-time Communication System)**. It provides a complete browser-based workbench and CLI tool for **IEC 61784-2 / IEC 61491**, enabling developers to build and dissect Layer 2 Ethernet telegrams (EtherType `0x88CD`), model isochronous motion cycle budgets down to 31.25 µs, inspect Service Channel (SVC) IDN drive parameters, and audit dual-ring redundancy and clock jitter boundaries.

---

## Key Capabilities

1. **MDT & AT Telegram Frame Builder & Dissector:**  
   - Full support for EtherType `0x88CD` with 12-byte Sercos III Telegram Headers (S3TH).  
   - Generates Master Data Telegrams (MDT) and Acknowledge Telegrams (AT) with IEEE 802.3 CRC-32 validation.  
2. **Isochronous Motion Timing & Jitter Sizer:**  
   - Models bus occupation, ring propagation delays (280 ns Fast Forward MAC latency per node), and UCC (Unified Communication Channel) TCP/IP bandwidth windows across cycle times from 31.25 µs to 1.0 ms.  
   - Hardware clock synchronization verification (\< 20 ns achieved, \< 100 ns IEC boundary).  
3. **Communication Phase State Machine (CP0..CP4):**  
   - Validates transition sequence from topology detection (CP0) to slave addressing (CP1), timing parameterization (CP2), service channel check (CP3), and real-time cyclic motion control (CP4).  
4. **Service Channel (SVC) & IDN Parameter Studio:**  
   - Accesses standard drive parameters (S-0-0047 Position Command, S-0-0051 Feedback, S-0-0036 Velocity, S-0-0080 Torque) across 7 standard elements.  
5. **10-Point Motion Network & Ring Safety Auditor:**  
   - Verifies dual-ring redundancy, jitter limits (\< 100 ns), timing overruns, drive velocity limits, Safe Torque Off (STO) monitoring, and CRC-32 integrity.  
6. **Multi-Target Master Code Generator:**  
   - Driver templates for Sercos SoftMaster (Linux RT-Preempt C++17), Python raw AF\_PACKET sockets, and Rexroth IndraMotion MLC.  
7. **Standalone Python 3 CLI Executable:**  
   - Zero-dependency CLI tool (`sercos-cli.py`) for automated test harnesses and field validation.

---

## Directory Structure

product\_192/

├── README.md                              \# Complete product overview

├── source-code/                           \# Web application suite

│   ├── index.html                         \# 5-tab responsive workbench

│   ├── sercos-frame-engine.js             \# MDT/AT framing & CRC-32 engine

│   ├── sercos-timing-calculator.js        \# Isochronous motion budget model

│   ├── sercos-network-auditor.js          \# 10-point motion network auditor

│   ├── sercos-forge.css                   \# Industrial red theme styling

│   └── app.js                             \# Interactive UI controller

├── build/                                 \# Executables & distribution

│   ├── sercos-cli.py                      \# Standalone Python 3 CLI tool (chmod \+x)

│   └── sercosforge-pro-v1.0.0.zip         \# Production distribution archive

├── documentation/                         \# Comprehensive manuals

│   ├── ARCHITECTURE.md                    \# Technical architecture & register specs

│   ├── USER\_GUIDE.md                      \# Complete usage and test workflows

│   ├── MONETIZATION\_AND\_MARKETING\_PLAYBOOK.md \# Commercial strategy & pricing

│   └── PROGRESS\_REPORT.md                 \# Cycle status & metadata

└── screenshots/                           \# Visual assets & diagrams

    ├── sercos-studio-preview.svg          \# High-resolution UI mockup

    └── sercos-architecture-diagram.svg    \# Subsystem block diagram

---

## Quick Start

### Web Application

Open `source-code/index.html` in any web browser. No server required.

### Command-Line Interface

\# Build MDT Telegram

./build/sercos-cli.py frame-build \--type MDT \--phase 4 \--cycle 100

\# Calculate Timing Budget

./build/sercos-cli.py timing-calc \--slaves 16 \--cycle-us 250

\# Run Network Safety Audit

./build/sercos-cli.py audit \--phase 4 \--dual-ring \--jitter 18.5 \--speed 3000 \--limit 4500

---

## License

MIT Open License (c) 2026 SercosForge Pro Contributors.