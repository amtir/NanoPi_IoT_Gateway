# NanoPi NEO2 as an IoT Gateway

An evaluation of the **FriendlyElec NanoPi NEO2** as a small, low-cost **IoT gateway**. It covers OS setup, headless access and bringing up the board's spare **UART** ports to talk to field devices from Python.

## Why the NanoPi NEO2

| Feature | Value |
|---------|-------|
| SoC | Allwinner H5, quad-core 64-bit ARM Cortex-A53 |
| GPU | Mali-450 (hexa-core) |
| RAM | 512 MB DDR3 |
| Network | Gigabit Ethernet |
| USB | 1 × USB host |
| Serial | 3 × UART (UART0 = debug console; **UART1 and UART2 free**) |

Its small size, Gigabit Ethernet and two free UARTs make it a good bridge between serial devices and a network or cloud backend.

## What the Evaluation Covers

1. **OS install**: flash the FriendlyCore image (Ubuntu Core, Linux 4.14) to an SD card with `dd` or Win32DiskImager.
2. **Headless boot & SSH**: the board has no video output, so you log in over SSH at the IP your router assigns.
3. **System checks**: package update, CPU architecture, disk usage, Python versions, loaded kernel modules.
4. **UART bring-up**: enable UART1 and UART2, install `pyserial`, list the serial ports and run a Python loopback/communication test.
5. **Hardware specs**: listed in the annex of the report.

The full step-by-step report with screenshots is [`docs/NanoPi_neo2_UART_IoT_Gateway.pdf`](docs/NanoPi_neo2_UART_IoT_Gateway.pdf). The editable source is the `.odt` file next to it.

## Quick Reference

```bash
# Flash the image (Linux)
sudo dd if=nanopi-neo2_friendlycore-xenial_4.14_arm64.img of=/dev/sdX bs=4M status=progress

# Log in (default FriendlyCore user: pi / pi, root / fa); change these passwords after first login
ssh root@<board-ip>

# Serial support for Python
sudo apt install python3-serial
ls /dev/ttyS*        # ttyS1 = UART1, ttyS2 = UART2
```

## Repository Structure

```
.
└── docs/
    ├── NanoPi_neo2_UART_IoT_Gateway.pdf   # Evaluation report
    └── NanoPi_neo2_UART.odt               # Report source
```

## Tech Stack

NanoPi NEO2 · Allwinner H5 · FriendlyCore (Ubuntu Core) · Linux · UART · Python (pyserial) · SSH

## Author

**Akram M'Tir**, [@amtir](https://github.com/amtir)
