# Job Card 2: Network Engineer

**Role:** Ethernet Subsystem Lead  
**Objective:** Enable Internet connectivity for the RISC-V Linux kernel.

---

## 1. Functional Requirements
* **Protocol:** Gigabit Ethernet (1000BASE-T).
* **Interface:** **RGMII** (Reduced Gigabit Media Independent Interface).
* **PHY Chip:** Select a PHY compatible with standard Linux drivers (e.g., Realtek or TI).
* **Magnetics:** Use an RJ45 Jack with integrated magnetics suitable for Gigabit speeds.

## 2. Constraints & Rules
* **Clock Pin Assignment (CRITICAL):**
    * The **RX_CLK** line *must* connect to a **MRCC** (Multi-Region Clock Capable) pin on the FPGA.
    * The **TX_CLK** line *must* connect to a **CC** (Clock Capable) pin.
    * *Action:* You cannot pick random pins. You must lookup these specific pin numbers from the datasheet.
* **I/O Voltage:** The PHY interface must operate at **3.3V** to match the FPGA Bank voltage.
* **Clock Frequency:** The RGMII interface runs at **125 MHz**. Trace lengths for Data[0-3] and Clock must be matched in the final PCB design.

## 3. Interfaces Needed
* **RGMII Bus:** TXD[0..3], RXD[0..3], TXC, RXC, TX_CTL, RX_CTL.
* **Management:** MDC, MDIO (2-wire interface).
* **Reset:** A GPIO pin to reset the PHY chip.

## 4. Breadboard Strategy
* **Feasibility:** **Zero.** (High-speed RGMII signals cannot work on breadboards).
* **Alternative:** For the prototype phase, wire a **SPI Ethernet Module** (10/100 Mbps) to the FPGA to allow the software team to test network drivers.