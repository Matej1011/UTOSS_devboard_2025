# Job Card 3: Video & Storage Engineer

**Role:** I/O & Peripherals Lead  
**Objective:** Provide visual output (HDMI) and persistent storage (MicroSD) for the OS.

---

## 1. Functional Requirements
* **Video Output:** HDMI (Type-A Connector).
    * *Signal:* TMDS (Transition Minimized Differential Signaling).
    * *Resolution Goal:* 720p or 1080p @ 60Hz.
* **Storage:** MicroSD Card Slot.
    * *Mode:* SPI Mode (1-bit) or SDIO Mode (4-bit).
    * *Capacity:* Support for SDHC cards (up to 32GB).

## 2. Constraints & Rules
* **HDMI Pin Assignment:**
    * HDMI signals come in pairs (Positive/Negative). You *must* use FPGA pins labeled as **Differential Pairs** (P and N).
    * *Action:* Request 4 pairs of Diff-Pair pins from the Lead Architect.
* **SD Voltage:** MicroSD cards run strictly at **3.3V**.
* **Logic Levels:** The FPGA Bank used for SD Card signals must be powered at 3.3V.

## 3. Interfaces Needed
* **HDMI:** 3 Data Pairs (D0, D1, D2) + 1 Clock Pair.
* **SD Card:** CS, MOSI, MISO, SCLK (for SPI mode) OR D0-D3, CMD, CLK (for SDIO mode).

## 4. Breadboard Strategy
* **Feasibility:** High.
* **Task:** Use breakout boards for the HDMI connector and MicroSD slot. Wire them to the FPGA headers using jumper wires. (HDMI might be glitchy on wires, but 640x480 resolution usually works).