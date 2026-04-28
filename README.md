# Kali Linux on Android with Raspberry Pi Zero 2 W --> Ethical Hacking without a "PC"
### 📌 Here you can see how I implemented a Raspberry Pi Zero 2 W with Kali Linux OS (for this board) using a Samsung tablet Tab S6 Lite 2022 Edition as terminal/monitor with VNC & Termux

<p align="center">
<img src="https://github.com/user-attachments/assets/0d1251fb-096a-48b1-bab8-cdc030bb3567" width="400">
</p>

<br>

## 🛒 Things we need
First, we need the following components to carry out the project:
- A `PC` for configuration
- `Raspberry Pi Zero 2W` or it could be also any Raspberry including (`Raspberry Pi Zero V1`, `Pi 3`, `Pi 4`, etc)
- `Power cable` for the Raspberry Pi
- `Raspberry Pi Imager` software for PC
- `SD card` (any size, 64GB recommended) for the Raspberry Pi
- `SD card holder` (to load the Kali Linux OS from Raspberry Pi Imager using your PC)
- `Tablet or mobile` (Android) device (in this case we used Samsung Tab S6 Lite 2022 version)
- `VNC` app for our device (RVNC Viewer on the Play Store) in which we are going to see the GUI of our OS
- `Termux` app for our device (to establish the SSH connection and commands, it's like our "PC terminal" but for Android)
- Connection to the `same Wi-Fi network` (there has to be the same Wi-Fi network between the tablet and the Raspberry Pi) --> In this case, I used my phone's mobile data network for both.

👉 ***Important:*** If using this mobile data connection, configure it and set it to the 2.4 GHz band, as the Raspberry Pi does not use 5 GHz.


<p align="center">
<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/2e1b3f0f-a52f-40e8-a7bd-dbb78dce595f" />
</p>

<br>
<br>

## 🔎 Step by step
### ⚙️ 1. *Operating System & SD Configuration*
Once you have everything you need, proceed as follows:
- Download `Raspberry Pi Imager` to your PC from: https://www.raspberrypi.com/software/. This software allows you to install any operating system on your board; in this case, Kali Linux for the Raspberry Pi Zero 2W.

- Once the app is installed, connect your SD card to an SD card reader and then connect the reader to your computer.

- Return to the Raspberry Pi software and go to the `OS` or "Operating Systems" menu. Select `Other specific-purpose OS` and find `Kali Linux` among the options. Then, search for `Raspberry Pi Zero 2W` (Kali Linux ARM image for the Raspberry Pi Zero 2W).

- Next, we select where we want to install the OS, and click on the SD card holder.

- We assign a hostname to our Raspberry Pi (this hostname is how it will be read when it appears on our cell phone's mobile data network).

- Then we fill in the information about our location and language.

- Following this, it will ask us to complete with the `username` for the Raspberry Pi (it is recommended to put `kali`) and its corresponding password (when we make the ssh connection the username will be placed in: *ssh username@IP*) (in addition, the password will serve to complete the ssh connection, asking for it twice for verification).

- Complete the information for the network connection to be used on the Raspberry Pi (it will ask for the SSID and password of the wifi network to which we will connect) (in my case I used my cell phone's mobile data network).

- Finally, we must select the option to activate `Enable SSH` along with the sub-option of `Use password authentication`, and click `Next`.

- Click on `Write` and wait a few minutes. Once you've done this, your SD card will be configured.

<br>

### 📟 2. *Raspberry Pi Zero 2 W initialization*
Once our SD card is configured, we'll insert it into our Raspberry Pi board. Before connecting it to the power supply, we need to make sure we've correctly configured our Wi-Fi network, where our two devices will connect (verify that it's a 2.4 GHz band connection and that the network has the same SSID and password that we entered in the Raspberry Pi installer). With that confirmed, we turn on the Wi-Fi network, wait a few minutes, and then power on our Raspberry Pi board. After a few minutes, the board will appear connected to the network with the `hostname` we assigned in the installer.

👉 ***Important:*** In my case, since I used my mobile data hotspot as my Wi-Fi network, if you use this method, you must be careful when powering the Raspberry Pi and then connecting it to the Wi-Fi network. If you unplug it (remove the power) and plug it back in while the Wi-Fi network is active, Kali Linux generates random MAC addresses during startup, and your mobile data network won't recognize your Raspberry Pi board. Instead of the `hostname` you assigned during the installer, you'll see a different MAC address (and its IP address won't be displayed either). Therefore, to fix this, you must reinstall the `OS` with the same configuration on the SD card and then reinsert it into the development board.

<br>

### 🗃️ 3. *Android Apps Installation & Execution*
To complete the connection between these two devices, we will need the following Android applications:
- Download `Termux`, which serves as a command-line terminal to control the Raspberry Pi from our Android device (this app alone would be sufficient, if we have knowledge of Linux commands, to manage the Raspberry Pi). With this app, we will update the terminal on both devices and establish the SSH connection. The steps to follow once installed are:

  --> On the Android device, run the following commands:
    * `pkg update && pkg upgrade` *(we update terminal)*
    * `pkg install openssh`
    * `ssh username@192.168.XX.XX` *(username = the one we assigned to the Raspberry Pi in the installer) @ (Raspberry Pi IP address that appears on the wifi network with X = complete with the digit that appears; if it is a mobile data wifi network, an IP address with the characteristic XX.XX.XXX.XX will appear instead of XXX.XXX.XX.XX)*
    
  --> Once completed up to this point, we will connect to the Raspberry Pi and proceed to execute the following commands in its terminal:
    * `sudo apt update` *(we update terminal)*
    * `sudo apt install tightvncserver` *(We downloaded the VNC service onto the board)*
    * `vncserver` *(We run the VNC service on the Raspberry Pi)*
    
- Next, we downloaded `VNC`, which allows us to use our Android device as a monitor for the Raspberry Pi.
    * To do this, we just need to enter the application on our device, register with an account, then tap on the `+` symbol, and enter any name and the IP address of our Raspberry Pi with a `:1` at the end. The format is (in my case of my mobile data as my wifi network) `XX.XX.XXX.XX:1`.

- And that's it! ✅ Now we can see our Raspberry Pi with Kali Linux as a computer on our Android device.

<br>

---

<br>

## 🚩 Actualizacion 26/04/2026 - Error 404 en Raspberry Imager con Kali Linux OS y Raspberry Pi Zero 2 W


👉 Nuevo fallo en Raspberry Imager: Al momento de querer instalar, en una placa Raspberry Pi Zero 2 W, el sistema operativo de Kali Linux que nos ofrece la misma aplicacion de instalador de imagenes de OS de Raspberry, ocurre un error 404. Esto se debe a que, hasta la fecha (26/04/2026), hay problemas con los servidores que le proporcionan a Raspberry Imager dicha imagen del sistema operativo de Kali Linux.

✅ Solucion? Descargar una imagen de Kali Linux (ARM) para la Raspberry Pi Zero 2 W, que es de 64 bits. Y luego, instalarla mediante la Raspberry Imager. Otra app opcional para flashear el OS en la placa es `BalenaEtcher`

<br>

### I hope you found this helpful and enjoyable. If so, leave a star ⭐ Best wishes and much success!

