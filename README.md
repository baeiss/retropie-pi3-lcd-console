# 🎮 RetroPie Portable Console Build (Raspberry Pi 3 + 3.2" TFT LCD)

<img width="500" alt="WhatsApp Image 2026-06-15 at 18 28 42" src="https://github.com/user-attachments/assets/70967302-3642-4d40-b454-154ad325b916" />

A fully functional, lag-free portable retro gaming console built from scratch using a Raspberry Pi 3 Model B and a WaveShare 3.2" SPI LCD.

## ⚙️ Hardware Components (BOM)
*   **SBC:** Raspberry Pi 3 Model B V1.2
*   **Display:** WaveShare SpotPear 3.2" RPi LCD V4 (Pin-to-pin SPI connection)
*   **Storage:** 16GB MicroSD Card (Minimum 8GB recommended for RetroPie OS and game ROMs)
*   **Controller:** 2.4GHz Wireless USB Gamepad


<img width="250" alt="WhatsApp Image 2026-06-15 at 18 27 02" src="https://github.com/user-attachments/assets/10709d94-4784-4581-a3a0-4292ebf0dcf5" />
<img width="250" alt="WhatsApp Image 2026-06-15 at 18 27 01" src="https://github.com/user-attachments/assets/0c836199-0a7d-42dc-bf1b-ac2d5cff5a56" />
<img width="250" alt="WhatsApp Image 2026-06-15 at 18 27 023" src="https://github.com/user-attachments/assets/e0601bf3-640d-4ec9-bb3e-7fdfece0340c" />


## 💾 OS Installation: Flashing RetroPie with Raspberry Pi Imager

To bring the hardware to life, the RetroPie operating system needs to be flashed onto the MicroSD card. Here is the step-by-step process using the official **Raspberry Pi Imager**:

1. **Insert the MicroSD Card:** Plug the 16GB MicroSD card into your computer's card reader.
2. **Launch the Imager:** Open the **Raspberry Pi Imager** application.
3. **Choose Device:** Click on "Choose Device" and select **Raspberry Pi 3**.
4. **Choose OS:** Click on "Choose OS", scroll down to **Emulation and game OS**, select **RetroPie**, and then choose the specific build for **Raspberry Pi 2/3/Zero 2 W**.
5. **Choose Storage:** Click "Choose Storage" and select your 16GB MicroSD card from the list.
6. **Write & Verify:** Click the **Write** button. The imager will download the OS, write it to the SD card, and verify the installation. Once the process is successfully completed, safely eject the card and insert it into the bottom slot of the Raspberry Pi 3.
