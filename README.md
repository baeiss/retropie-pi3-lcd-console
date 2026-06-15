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
> **📌 Official Raspberry Pi Imager download link:** http://raspberrypi.com/software/

1. **Insert the MicroSD Card:** Plug the 16GB MicroSD card into your computer's card reader.
2. **Launch the Imager:** Open the **Raspberry Pi Imager** application.
3. **Choose Device:** Click on "Choose Device" and select **Raspberry Pi 3**.
4. **Choose OS:** Click on "Choose OS", scroll down to **Emulation and game OS**, select **RetroPie**, and then choose the specific build for **Raspberry Pi 2/3/Zero 2 W**.
5. **Choose Storage:** Click "Choose Storage" and select your 16GB MicroSD card from the list.
6. **Enable SSH & Wi-Fi (Crucial Step):** Before proceeding, click the **OS Customization (Gear) icon** (or click "Next" and select "Edit Settings" depending on the Imager version). 
   * Check **Enable SSH** (Use password authentication).
   * Check **Configure wireless LAN** and enter your Wi-Fi SSID, password, and correct Wireless LAN country.
7. **Write & Verify:** Click the **Write** button. The imager will download the OS, write it to the SD card, and verify the installation. Once the process is successfully completed, safely eject the card and insert it into the bottom slot of the Raspberry Pi 3.

## 🖥️ Enabling the 3.2" TFT LCD (Driver Installation)

> ⚠️ **Important Note:** On initial boot, the 3.2" TFT screen will remain blank (white) as RetroPie defaults to HDMI output. You will need to install the WaveShare drivers to route the screen via GPIO pins.

>
> You can do this using one of the two methods below. **Method A (Headless)** is strongly recommended for a cleaner setup.

### Method A: Headless Setup via SSH (Recommended)
If you checked **"Enable SSH"** and **"Configure Wireless LAN"** in Raspberry Pi Imager before flashing the SD card, you don't need an external monitor or keyboard.

**Find Your Pi's IP Address:** Turn on the Pi and wait a minute.
1. Open CMD on your computer and type `ping retropie.local`. The resulting IP address is your Pi's address.
2. **Connect via SSH:** [PuTTY] Download and open https://www.putty.org/. Enter the IP address, ensure the Port is 22, and click Open. Log in with your configured credentials.
3. **Install drivers:** Run the following commands in the terminal:

```bash
git clone https://github.com/waveshare/LCD-show.git
cd LCD-show/
chmod +x LCD32-show
./LCD32-show
```

### Method B: Direct Setup via HDMI & Keyboard (No SSH)
If you skipped the SSH configuration during the flashing process, you must use an external monitor and a physical keyboard to install the drivers.

1. **Hardware Connections:** Connect the Raspberry Pi to a monitor or TV using an **HDMI cable**. Plug in your **USB Gamepad** and a **USB Keyboard**, then power on the device. (The system will output video via HDMI normally).
2. **Map the Gamepad:** EmulationStation will boot up and display a welcome screen. Hold any button on your gamepad and follow the on-screen prompts to map your controls. Once finished, you will reach the main menu.
3. **Connect to Wi-Fi:** * Using your gamepad, navigate to the **RetroPie** menu and select **WIFI**.
   * First, select **Set Wi-Fi Country** and choose your region. *(Important: The Pi cannot connect to the internet until the country is set).*
   * Next, select **Connect to WiFi network**, choose your network, and type your password using the USB keyboard.
4. **Access the Terminal:** Once connected to the internet, exit back to the main EmulationStation screen. Press **`F4`** on your USB keyboard to close the graphical interface and drop into the command-line console. *(Note: This action requires a physical keyboard; the gamepad cannot trigger this).*
5. **Install the TFT Drivers:** Type the following commands exactly as shown, pressing `Enter` after each line:

```bash
git clone https://github.com/waveshare/LCD-show.git
cd LCD-show/
chmod +x LCD32-show
./LCD32-show
```

## 🎮 Fixing In-Game Controller Issues (Input Reset)

If you followed **Method B** and used a physical keyboard during the setup, you might encounter an issue where your gamepad works perfectly in the main menu but **does not work or is completely unresponsive inside the games**. To fix this, you need to wipe the mixed input configurations.

Here is the step-by-step fix:

1. **Access RetroPie Setup:** From the main EmulationStation menu, navigate to the **RetroPie** screen and select **RetroPie Setup**.
2. **Configuration Tools:** Scroll down the list and select **Configuration Tools**.
3. **Find EmulationStation:** Scroll down until you find **emulationstation** and open it.
4. **Clear Configurations:** Select **Clear/Reset Emulation Station input configuration**. It will prompt a warning; confirm it by selecting **Yes**, then hit **OK**.
5. **Safe Reboot (CRITICAL STEP):** *Do not press the back button repeatedly to exit!* Since the configs are wiped, your controller is now disabled. Pulling the power cord can corrupt your SD card. Instead, select **Cancel**, then **Back**, and scroll to the bottom of the main list to select **Perform reboot**.
6. **Fresh Remap:** When the system reboots, you will be greeted by the initial EmulationStation Welcome screen. Hold any button on your gamepad to freshly remap your inputs. 

Your gamepad will now work perfectly both in EmulationStation and inside all game emulators!
