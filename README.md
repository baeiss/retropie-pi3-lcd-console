# 🎮 RetroPie Portable Console Build (Raspberry Pi 3 + 3.2" TFT LCD)

<img width="1200" height="1600" alt="WhatsApp Image 2026-06-15 at 18 28 42" src="https://github.com/user-attachments/assets/70967302-3642-4d40-b454-154ad325b916" />

A fully functional, lag-free portable retro gaming console built from scratch using a Raspberry Pi 3 Model B and a WaveShare 3.2" SPI LCD. This project includes custom 3D-printed housing and a critical kernel-level driver fix for touchscreen input conflicts.

## ⚙️ Hardware Components (BOM)
*   **SBC:** Raspberry Pi 3 Model B V1.2
*   **Display:** WaveShare SpotPear 3.2" RPi LCD V4 (Pin-to-pin SPI connection)
*   **Controller:** 2.4GHz Wireless USB Gamepad


<img width="3840" height="5120" alt="WhatsApp Image 2026-06-15 at 18 27 02" src="https://github.com/user-attachments/assets/10709d94-4784-4581-a3a0-4292ebf0dcf5" />
<img width="3840" height="5120" alt="WhatsApp Image 2026-06-15 at 18 27 01" src="https://github.com/user-attachments/assets/0c836199-0a7d-42dc-bf1b-ac2d5cff5a56" />
<img width="3840" height="5120" alt="WhatsApp Image 2026-06-15 at 18 27 022" src="https://github.com/user-attachments/assets/65039314-ec2d-4cf7-8ea5-3c6de1204504" />
<img width="3840" height="5120" alt="WhatsApp Image 2026-06-15 at 18 27 023" src="https://github.com/user-attachments/assets/e0601bf3-640d-4ec9-bb3e-7fdfece0340c" />


## 🚨 The Challenge: "Axis Spamming" Kernel Bug
When integrating the TFT touchscreen directly via GPIO, the Linux kernel (Debian/RetroPie) mistakenly recognizes the touch panel as a primary game controller. This creates an infinite loop of "joystick inputs" (Axis Spamming), which completely freezes EmulationStation and rejects any external USB gamepads. Standard UI configurations cannot bypass this hardware conflict.

## 🛠️ The Solution: UDEV Rule Override
To fix this, I bypassed the frontend and directly manipulated the Linux device manager (`udev`) to isolate the touchscreen driver at the kernel level. 

By creating a custom rule, we instruct the system to strip the "joystick" identity from the touch panel permanently, while preserving the display output:

```bash
# Fix for TFT Touchscreen Controller Conflict
# Add this rule to /etc/udev/rules.d/99-touchscreen-joystick.rules

SUBSYSTEM=="input", ATTRS{name}=="ADS7846 Touchscreen", ENV{ID_INPUT_JOYSTICK}=""
