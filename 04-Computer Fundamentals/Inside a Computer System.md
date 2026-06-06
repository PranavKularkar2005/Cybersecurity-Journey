# 💻 TryHackMe - Inside a Computer System

## 📖 Overview

This repository contains my notes and walkthrough for the **"Inside a Computer System"** room from the **Computer Fundamentals** module in TryHackMe.

This room introduces the core components of a computer system and explains how they work together. It also covers the computer boot process, from pressing the power button to loading the operating system.

---

## 🎯 Learning Objectives

After completing this room, I learned:

* The major hardware components of a computer
* The role of each component inside a system
* How a computer boots up
* What firmware and UEFI do
* The purpose of POST (Power-On Self-Test)
* How an operating system is loaded

---

# 📝 Task 1: Introduction

Before securing a system, it is important to understand what is being protected.

TryHackMe compares a computer system to a castle:

* Components are like different rooms in a castle.
* Each room has a specific purpose.
* Understanding the structure helps us secure it effectively.

### Key Takeaway

Understanding computer fundamentals is essential before learning cybersecurity concepts.

---

# 📝 Task 2: Inside a Computer System

A computer consists of several hardware components that work together.

## Computer Components

### 🧠 CPU (Central Processing Unit)

**Role:** The Brain of the Computer

Responsibilities:

* Executes instructions
* Performs calculations
* Processes data
* Controls system operations

---

### ⚡ RAM (Random Access Memory)

**Role:** Short-Term Memory

Responsibilities:

* Temporarily stores active programs and data
* Provides fast access to information
* Clears data when power is removed

---

### 🎮 GPU (Graphics Processing Unit)

**Role:** Visual Processing

Responsibilities:

* Renders images and videos
* Handles graphics-intensive tasks
* Improves gaming and graphical performance

---

### 💾 Storage (SSD/HDD)

**Role:** Long-Term Memory

Responsibilities:

* Stores operating system
* Stores applications
* Stores files permanently

Types:

* SSD (Solid State Drive)
* HDD (Hard Disk Drive)

---

### 🔌 PSU (Power Supply Unit)

**Role:** Heart and Lungs of the Computer

Responsibilities:

* Supplies power to all components
* Converts AC power to DC power

---

### 🌐 Network Adapter

Responsibilities:

* Connects computer to networks
* Enables internet communication

---

### ⌨️ Input/Output Devices

Examples:

* Keyboard
* Mouse
* Monitor
* Printer
* Speakers

These devices allow users to interact with the computer.

---

## Task Flag

```text
THM{4llpccomp0n3nts1d3nt1f13d}
```

---

# 📝 Task 3: What Happens When You Press the Start Button?

The boot process starts when the power button is pressed.

---

## Step 1: Press Power Button

* User presses the power button.
* PSU begins supplying power to components.

---

## Step 2: Firmware Starts

The system firmware initializes hardware.

Modern systems use:

* UEFI (Unified Extensible Firmware Interface)

Older systems use:

* BIOS (Basic Input/Output System)

UEFI has largely replaced BIOS.

---

## Step 3: POST (Power-On Self-Test)

The firmware performs diagnostic checks.

Checks include:

* CPU
* RAM
* Storage Devices
* Connected Hardware

Purpose:

* Verify components are functioning correctly.

---

## Step 4: Select Boot Device

UEFI checks the configured boot order.

Examples:

1. SSD
2. HDD
3. USB Drive
4. Network Boot

The first valid boot device is selected.

---

## Step 5: Start Bootloader

The bootloader loads the operating system into RAM.

Examples:

* Windows Boot Manager
* GRUB (Linux)

Once loaded:

* Control is transferred to the operating system.
* The user interface becomes available.

---

## Boot Process Summary

```text
Power Button
      ↓
Firmware (UEFI/BIOS)
      ↓
POST
      ↓
Select Boot Device
      ↓
Bootloader
      ↓
Operating System
```

---

## Task Flag

```text
THM{pc5ucce55fully5t4rt3d}
```

---

# 🔑 Key Takeaways

* CPU acts as the brain of the computer.
* RAM stores temporary working data.
* SSD/HDD stores data permanently.
* PSU powers the entire system.
* UEFI initializes hardware during startup.
* POST verifies component functionality.
* The bootloader loads the operating system.
* Understanding computer hardware is fundamental for cybersecurity.

---

# 🛠 Skills Gained

* Computer Hardware Fundamentals
* System Architecture
* Boot Process Understanding
* UEFI & BIOS Concepts
* Operating System Loading Process
* Cybersecurity Foundations

---

# 📚 Platform

* TryHackMe
* Learning Path: Pre-Security
* Module: Computer Fundamentals
* Room: Inside a Computer System

---

# 🚀 Status

✅ Completed Successfully

